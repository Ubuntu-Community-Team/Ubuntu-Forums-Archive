---
title: "Tunnel X from Gutsy to Leopard (keyboard problems)"
date: 2007-12-19
forum: General Help
---

### Post by hornett on 2007-12-19
I want to use my Macbook (running OSX Leopard) to run some X programs on my server (using Gutsy).

I can access some apps fine via SSH. Everything works nicely.

The problem I have is that if I try to use certain Gnome programs, the gnome-settings-daemon starts and after that, I can't use the keyboard properly. I get numbers when I press some keys, other keys do wierd things like close windows, minimize things etc.

What can I do to make this work? I tried changing the gnome-keyboard settings to 'Macintosh' or 'Macbook/Macbook Pro' from the control panel in Gutsy, but that just gives me a lot of xkb errors when I start the Xserver, and prevents the machine's real keyboard from working.

Any ideas? I'm stumped at this point. I've never had keyboard problems forwarding X before...
:confused::confused::confused:

Thanks!

---

### Post by kennythegeek on 2008-01-07
the thing is that the keymaps don't fit with each other
Log onto ssh with x forwarding (ssh -Y server) and type xmodmap -pke > ~/.keymap
Then you need to make it run xmodmap ~/.keymap when you start an X application
If you use xdmcp, you can just add "xmodmap ~/.keymap" to ~/.xsession.
Otherwise you need to make it run xmodmap after you start an X application.
I have made a little applescript to start gnome-panel and fix that little error (Only works if the connection is password-less or uses a public/private key pair) :
```
set the username to "Your Username"
set the defaultIP to "Your Servers IP"
set the defaultAction to "xmodmap ~/.keymap"
set the XAction to "gnome-panel"
set the shellAction to "uxterm"
set the parameters to "-fnX"
display dialog "Settings" default answer defaultIP buttons {"Cancel", "Open Shell", "Connect"} default button 3 with icon 1
copy the result as list to {adress, button_pressed}
if button_pressed is not "Cancel" then
	if button_pressed is "Connect" then
		set action to XAction
	else if button_pressed is "Open Shell" then
		set action to shellAction
	end if
	set the command to "ssh " & parameters & " -l " & username & " " & adress & " '" & action & " & " & defaultAction & "'"
	try
		do shell script command
	on error the error_message number the error_number
		if the error_number is not -128 then
			set the error_text to "Error: " & the error_number & "." & the error_message
			display dialog the error_text buttons {"Cancel"} default button 1
		else
			error number -128
		end if
	end try
else
	display dialog "User cancelled" buttons {"OK"} default button 1
end if
```
Open script editor, insert that into it (and change the 2 fields in the start), choose "Save as", type a name, and choose application-package (or something, my OSX is danish :P ).
Now you can run that, and choose connect, and it would do the job.

the thing is just: Every time you make a xsession (when you run the first X application), you need to run xmodmap ~/.keymap. so if you start in ssh with running gnome-panel you could run:
gnome-panel 1>/dev/null 2>/dev/null & xmodmap ~/.keymap

---

### Post by hornett on 2008-01-07
Thanks for the detailed information! That really is excellent.  :KS :KS :KS 

I'm away from home at the moment but I will definitely be using that script. 

Cheers!
Andy :)

---

### Post by abyhoe on 2008-04-03
I too had the same problem after I upgraded from Tiger to Leopard. Thanks for the post and the solution! It's great and I am a happy Mac and Ubuntu user again. :)  :popcorn:
--
Adrian Hoe

---

