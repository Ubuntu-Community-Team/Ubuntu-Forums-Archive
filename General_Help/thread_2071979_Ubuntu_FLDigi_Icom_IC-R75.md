---
title: "Ubuntu FLDigi Icom IC-R75"
date: 2012-10-16
forum: General Help
---

### Post by tm-hart on 2012-10-16
[COLOR="Red"]SETUP NOTES FOR FLDigi and Icom IC-R75 [/COLOR]

**Summary**: The Icom IC-R75 and FLDigi software form a solid partnership after installation and setup.  CW, BPSK-31 and RTTY-45 signals have been received during testing.  Two cables connect the receiver to the computer:
	
      a.  A USB to Serial cable for CAT commands.  
      b. An audio cable from receiver to computer for received signal audio.

Note: Three types of audio cables were tested:

1. A stereo cable from the external speaker connector to the computer microphone connector.
2. A cable with mono (receiver) and stereo connector (computer) from receiver to computer.
3. A Y-adapter in the external speaker connector for a speaker plus cable 1 or 2.

	[COLOR="Red"]Part I. Receiver settings:[/COLOR]

My R75 is set for:
1. Preamp 2.
2. USB.
3. AGC on.
4. IF Filter is “wide” (2.8 KHz).

	[COLOR="Red"]Part II. Hamlib setup and CONFIGURATION menu settings:
[/COLOR]
Hamlib controls the receiver.  
CAT commands work via the USB to Serial cable  at 9600 baud and 1 stop bit.
The DEVICE setting is /dev/tty/USB0.
Audio-Devices are set for PORT AUDIO.  
The “capture” and “playback” drop down menu options should be the ones matching your sound card.
The terminal command “aplay -l” will list installed sound cards.  

	[COLOR="Red"]Part III. Operating System Settings:[/COLOR]

A number of on-line postings advise making changes to the “/etc/group” file.
Edit the file to add yourself to the group for two lines: (1) “dialout:x:20:” and (2) “tty:x:5:”.  
Assume that your login name is “username”; make these edits:
		dialout:x:20:username
		tty:x:5:username

Save the file, log out and log back in.  Instead of logging out-in, rebooting the computer  and logging back in will also reset your permissions.

It is easy to install FLDigi via Synaptic. Then, start the program from either a terminal prompt by typing “fldigi”or from Dash Home.  For future convenience, consider locking FLDigi to the Launcher.

	[COLOR="Red"]Part IV. Odds and ends:[/COLOR]
The top line menu choice “Configure – Colors & Fonts” allows customization of screen appearance.  A variety of colors for the receive and transmit panels are available along with various fonts.  I like the Arial font size 22 with beige backgrounds for both panels.  Consider minimizing the transmit panel.  It will not be needed with the R75 receiver.

The “Signal Range (dB)” slider on lower left of the FLDigi main screen is helpful in setting input signal strength.  By increasing or decreasing the setting, incidental noise can be minimized.  In general, there should be good contrast between background and signal streams .

It is easy to rename and rewrite the MACRO buttons on the FLDigi screen.  The manual explains the options.  Some macros examples:

Macro to change frequency:
	<QSY:7070>

Note: According to on-line sources, PSK-31 frequencies are: 3850, 7070, 10138, 14070, 18100, 21070 and 28120 KHz.

Macro to clear receive panel:
	<CLRRX>

Macros to change modes to CW, PSK or RTTY (45.45/170):
	<MODEM:CW>
	<MODEM:BPSK31>
	<MODEM:RTTY>

On the WATERFALL-DISPLAY menu, un-check the “Always show audio frequencies” option to display RF frequencies on the waterfall instead of audio frequencies.  

When Hamlib is running, the name of the control file will appear above the VFO frequency panel on the upper left of the screen.  When Hamlib is not working, the tag ”Enter Xcvr Freq.” will appear. 

**Personal note**: My thanks and congratulations go to Dave Frees / W1HKJ and his team for their efforts in creating FLDigi.  This is an excellent program that is a boon to the community.

---

