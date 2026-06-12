---
title: "launch shortcut doesn't work"
date: 2018-02-08
forum: General Help
---

### Post by dwieberd on 2018-02-08
I successfully installed an application, but the only way I've been able get it to run is by navigating down thru the file hierarchy and clicking on the executable name. I don't really want to have to do that each time I launch it. I've tried dragging a copy to the desktop and clicking it. I've tried locking it to the Launcher. Nothing works. Even clicking on the icon in Dash does nothing. Any idea what is wrong? Please help.

---

### Post by irv on 2018-02-08
First, what is the application?
Second, how did you install it?
Third, what version are you using of Ubuntu?
It sounds like you did something wrong when installing it.
Give us this information and someone should be able to help.

---

### Post by dwieberd on 2018-02-08
Thanks irv. 

1) It's Xilinx's FPGA development system called ISE. 
2) I ran an install script from a terminal shell as in: "./xsetup". Prior to that I ran a script called "settings64.sh" per the instructions.
3) 16.04 LTS.

Thanks for any help you can give.

---

### Post by #&amp;thj^% on 2018-02-08
You should have a folder in your /home/your_user_name Directory Called " ISE ".
In there you will/should find a version number....can you tell us what version you are now using?
It might be as easy as changing the script for Desktop Shortcut a bit. (Best case Senrio)

---

### Post by dwieberd on 2018-02-08
There is no user name directory under /home, only Desktop, Documents, Downloads, etc.  Perhaps this is because I bought the laptop pre-installed with Ubuntu?
But I do know the ISE version is 14.7. & it installed under /opt/Xilinx. Does that help?

---

### Post by #&amp;thj^% on 2018-02-08
Welp I installed mine in "~/username" where **username=me**.
I then Created an ISE 14.7.desktop entry in "~/.local/share/applications" with the contents:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=/home/user/Xilinx/14.7/ISE_DS/ISE/data/images/pn-ise.png
Name=ISE 14.7
Exec=bash '/home/user/Xilinx/14.7/ISE_DS/run_ise.sh'
Comment=Runs Xilinx ISE 14.7
```
I do remember needing xfonts-100dpi, xfonts-75dpi installed.(But they are usually installed by default)

---

### Post by dwieberd on 2018-02-08
Sorry, I was wrong about not having a username dir. I was basing that on the file manager gui. When I tried it in a terminal window I could see it.
The closest thing I could find to the location you mentioned is /usr/local/share. But there is no applications directory under share. Should I create one and add a file with contents similar to yours (with path names changed, of course)?
Should the filename be called "ISE 4.7.desktop" or am I misunderstanding? 
Also I couldn't find any script named "run_ise.sh" on my installation. If I click on a file just called "ise" buried down in the hierarchy everything seems to work fine, but I always have to navigate there manually. There has to be better way, even if it doesn't involve the official Launcher. I'm just trying to launch it easier. Thanks.

---

### Post by dwieberd on 2018-02-08
If I start a terminal shell by right-clicking the desktop and then type "/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise" in the shell ISE starts up fine. 

Why doesn't it work to add a file to the desktop containing the same command? I have checked he executable box in the properties window. What am I missing?

---

### Post by #&amp;thj^% on 2018-02-08
>  But there is no applications directory under share. Should I create one and add a file with contents similar to yours (with path names changed, of course)?

Humm? well lets have a look with:
```
cd ~/.local/share/applications
```
And then;
```
ls
```
Sorry for the delay I just got busy, and may have to leave you for the nite in a short while, but I won't abandon you.

---

### Post by dwieberd on 2018-02-08
Ok. I don't understand why "applications" is there now. As you can see: don't assume that I know anything. :)

Here's the response:

username@username-XPS-13-9360:~$ cd ~/.local/share/applications
[email]username@username-XPS-13-9360:~/.local[/email]/share/applications$ ls
chrome-aohghmighlieiainnegkcijnfilokake-Default.desktop  chrome-pjkljhegncpnkpknbcohdijeoejaedia-Default.desktop
chrome-apdfllckaahabafndbhieahigkjlhalf-Default.desktop  mimeapps.list
chrome-blpcfgokakmgnkcojhhkbfbldkacnbeo-Default.desktop  _pn.desktop

I didn't notice any delay. Thank you again for your help though!

---

### Post by #&amp;thj^% on 2018-02-09
> **dwieberd said:**
> Ok. I don't understand why "applications" is there now. As you can see: don't assume that I know anything. :)

I didn't notice any delay. Thank you again for your help though!

That's Ok, I/we was all new here once.:)
The reason why you did not see it was because the dot "." in front of anything means it is what is called hidden files/folders.
To view hidden files with your file manager just use the keyboard combo>>>(Ctrl+h).
********
Well now I would like to see the script you use for your shortcut, if you would paste that back here to see.
Just a Heads-up, I will be in and out of the forums all day today.(Duty Calls)

---

### Post by dwieberd on 2018-02-13
Now I'm sorry for the delay. I forgot to look for 'page 2". Duh.

Here's what I tried to use:

/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise

If I type (or copy and paste) into a terminal window, it works. But clicking on the icon for the script on the desktop seems to do nothing.

---

### Post by #&amp;thj^% on 2018-02-13
I would still like to see the script for the shortcut, Not the code you use.:) "/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise"

Here is what works for ISE 14.7. I have just changed 'Exec' parameter of the .desktop file.

```
Exec='/home/user/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise'
```

To be able to run ISE, you should set environment variables first running "**source settings(32/64).sh**" in the ISE_DS folder.

It seems to works fine for me.
I'm running a XFCE desktop.

---

### Post by dwieberd on 2018-02-13
I think I did run that settings64.sh script during/after the install. I don't need to run that script every time I start ISE do I?
I guess I thought the startup script for ISE and the code were the same thing. Maybe that's part of my problem.
I created a file on the desktop called ise.sh. The contents were simply "/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise"  [I guess I'm too used to Windows shortcuts, so I thought it should work.]
I edited the properties for ise.sh and checked the 'allow executing as program' box. After seeing your last reply I tried adding the Exec='...' to the file/script contents. It still doesn't work when I double-click the icon for the script.

I don't know how to add the cool code box like you had. But if I did it would now look just like yours except with "/home/user" replaced with "/opt". That is my script now. As I said: initially I did not have the "Exec=' but that does  not seem to help.

I think I'm probably using the Gnome desktop. I'm not sure how to know. As I said the laptop came with Ubuntu installed. I don't think it ever asked me what desktop I wanted.

I hope this is what you were asking for.

---

### Post by #&amp;thj^% on 2018-02-14
> **dwieberd said:**
> I think I did run that settings64.sh script during/after the install. I don't need to run that script every time I start ISE do I?

No!
> **dwieberd said:**
> 
I guess I thought the startup script for ISE and the code were the same thing. Maybe that's part of my problem.
I created a file on the desktop called ise.sh. The contents were simply "/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise"  [I guess I'm too used to Windows shortcuts, so I thought it should work.]

I just needed to see how you created the shortcut, and now i see what is going on with yours.

Open up a terminal and enter

```
cd /opt/Xilinx/14.7/ISE_DS
sudo -H gedit run_ise.sh
```

In the text editor paste the following code.

```
#!/bin/bash
. /opt/Xilinx/14.7/ISE_DS/settings64.sh
ise
```

Save and close the file. Then back in the terminal enter the following.

```
sudo chmod +x run_ise.sh
```

This will make the file you just created executable.
> **dwieberd said:**
> 
I don't know how to add the cool code box like you had. 
See my Signature for Code Tags! ;)
> **dwieberd said:**
> 
I think I'm probably using the Gnome desktop. I'm not sure how to know. 
To find that out use:
```
echo $DESKTOP_SESSION
```
Let us know how things go with this. ;)

---

### Post by dwieberd on 2018-02-15
I get the following warnings when saving the file:

(gedit:31875): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:31875): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:31875): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:31875): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

I assumed we don't want a space between . and /opt in run_ise.sh. But clicking on the script still does nothing. Shouldn't there be a /bin/lin64 in the text of the script somewhere?

When I do "echo $DESKTOP_SESSION" I just get "ubuntu" in response .

---

### Post by #&amp;thj^% on 2018-02-16
You know I'm not real sure about Unity and the shortcut.
But I think this should work or at least make the command  smaller.:D
The installer creates a script file for you called settings.sh. This file sets up your environment. I used this to create a startup script for ISE as follows: 
Run:
```
cp /opt/Xilinx/settings.sh /usr/local/bin/startise 
```
2.
```
echo "export DISPLAY=:0" >> /usr/local/bin/startise 
```
3.
```
echo "exec ise" >> /usr/local/bin/startise 
```
4.
```
chmod +x /usr/local/bin/startise  
```

5.Start the application with: "**startise**"
```
startise
```

---

### Post by dwieberd on 2018-02-16
Well, I got as far as #1, sort of. It didn't work as given so I tried:
```

sudo cp /opt/Xilinx/14.7/ISE_DS/settings64.sh /usr/local/bin/startise

``` That worked, but then:
```

sudo echo "export DISPLAY=:0" >> /usr/local/bin/startise

```
resulted in:
```
 bash: /usr/local/bin/startise: Permission denied
```

---

### Post by #&amp;thj^% on 2018-02-19
> **dwieberd said:**
> Well, I got as far as #1, sort of. It didn't work as given so I tried:
```

sudo cp /opt/Xilinx/14.7/ISE_DS/settings64.sh /usr/local/bin/startise

``` That worked, but then:
```

sudo echo "export DISPLAY=:0" >> /usr/local/bin/startise

```
resulted in:
```
 bash: /usr/local/bin/startise: Permission denied
```
Did you forget to make executable with:
```
chmod +x /usr/local/bin/startise
```
With this method it should work on all desktop environments EG: XFCE Mate LXDE openbox.
And it does work for me anyway:
```
echo $DESKTOP_SESSION
xfce

```

---

### Post by dwieberd on 2018-02-19
I thought making it executable was step 4. I didn't even get past step 2.
I guess I just don't understand why this is so difficult. 
I have been using ISE in this environment for several days already. I have successfully routed several iterations of an FPGA.
I have a file on the desktop whose contents = "/opt/Xilinx/14.7/ISE_DS/ISE/bin/lin64/ise".
I leave the file open on the desktop in gedit. I select the window, type ^A to select the contents ^C to copy to the clipboard,
open a terminal window, right-click and select "paste" and ISE starts just fine. If I just suspend between sessions I don't even have to do all this; ISE just stays open on the desktop. I guess I'll just keep doing it this way. It just seems really strange that it should be so difficult to make a shortcut/link that does the same thing with a single click. Doesn't speak very well for Unity. Maybe that's why Canonical is abandoning it. Someday I'll switch to Gnome, but it's not worth it to me at the moment; as long as I can make progress as is.
Thanks for trying anyway.

---

