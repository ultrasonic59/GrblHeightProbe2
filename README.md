# [Update: Has been replaced by OpenCNCPilot](https://github.com/martin2250/OpenCNCPilot)

# GrblHeightProbe2

This is GRBL Height Probe, the improved version of my PCB autolevelling toolchain for GRBL-based CNC mills

If you're using a CNC mill to isolate tracks on a PCB, you'll run into problems where the surface of the PCB isn't entirely flat, so you'll end up with broken or shorted traces.
GRBL Height Probe aims to eliminate that problem by first probing the surface, then adjusting any GCode file to follow the surface exactly.

The probing data is stored in an array of floats, the exact values are obtained via bilinear interpolation between the four nearest points.
The actual machine coordinates are related to the position in the array via the GridSize (distance between points) and the Offset (position of lower left point)

All GCode Commands whose length exceeds the GridSize are split up into sections smaller than the GridSize. This includes Arcs.

In the input files, arcs can be defined via center (IJ) coordinates or by a radius (R).
The output file will always use IJ notation, absolute coordinates and metric units. Both relative coordinates and imperial units are supported, but are converted to the aforementioned format.

###Supported G-Codes:
*G0, G			linear motion
*G2, G3			arc motion
*G20, G21		units
*G90, G91		distance mode

unsupported g-codes will be preserved in the output

Quick overview on youtube:  
[![Video](http://img.youtube.com/vi/kzXzvcUAuus/0.jpg)](http://www.youtube.com/watch?v=kzXzvcUAuus)

Example output (vastly exaggerated unevenness):  
![Chilipeppr Screenshot](http://i.imgur.com/iOl1Bn6.png)

If you have trouble finding the download: https://github.com/martin2250/GrblHeightProbe2/releases/latest

Credits:
	Start, Pause Icons: designed by FreePik (http://www.freepik.com)
	Vector3 class by R Potter on codeplex (http://www.codeproject.com/Articles/17425/A-Vector-Type-for-C)

Since this project did get some attention, I'll include a donation button. I'm currently working on OpenCNCPilot which will replace this program and also act as a G-Code streamer, so you won't have to switch between HeightProbe and Universal GCode Sender anymore.  
Please note that my programs will always be (ad)free  
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=7F783UGMYHRWN)
