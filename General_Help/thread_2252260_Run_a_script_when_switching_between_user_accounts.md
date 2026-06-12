---
title: "Run a script when switching between user accounts"
date: 2014-11-10
forum: General Help
---

### Post by xmbwd on 2014-11-10
I have a script that uses xmodmap to switch the keys on a Mac keyboard so that the "apple/command" button functions as CTRL and vice-versa.  The script runs on startup and on resume from suspend (see below).  But I just added a new account to the computer, and when I switch between accounts, the keys revert to their original settings.  Is there something that I can do to make this script run on user switch?

Alternatively, is there some way to switch these keys without a script?  I thought the script was the best way to go, but there is always more than one way to do things in Ubuntu.  

Thanks.  


```
**Put the following in ~/.Xmodmap**:
remove control = Control_L
remove mod4 = Super_L Super_R
keysym Control_L = Super_L
keysym Super_L = Control_L
keysym Super_R = Control_L
add control = Control_L Control_R
add mod4 = Super_L Super_R

**To test, run the command**:
xmodmap ~/.Xmodmap

**To make it run at startup** 
create a script file “xmodmap.sh”
    #!/bin/bash   
    xmodmap /home/user/.Xmodmap
chmod +x that file
gedit /home/user/.config/autostart/user_xmod.desktop
    [Desktop Entry]
    Type=Application
    Name=My Script
    Exec=sh -c "sleep 5 && /home/user/xmodscript.sh" ## this invokes a shell construct so you can use shell commands as in terminal (http://askubuntu.com/questions/99291/execute-complex-command-in-desktop-file-unity-quicklist).  The sleep is necessary for some reason.##
    Icon=system-run
    X-GNOME-Autostart-enabled=true
    Name[en_US]=user_xmod.desktop

**To make it run at wake from suspend:**
sudo -i
cd /etc/pm/sleep.d
gedit 11_xmodscript.sh  
(Paste:) 
#!/bin/bash
case $1 in
    hibernate)
        echo "Hey guy, we are going to suspend to disk!"
        ;;
    suspend)
        echo "Oh, this time we're doing a suspend to RAM. Cool!"
        ;;
    thaw|resume)
        echo "oh, suspend is over, we are in $1 phase..."
            # Set Display #
    DISPLAY=:0.0 ; export DISPLAY
    /bin/su user -c "sleep 3; /usr/bin/xmodmap /home/user/.Xmodmap" &
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac
chmod +x 11_xmodscript.sh
```

---

### Post by xmbwd on 2014-11-13
Well, I didn't get any responses to this.  Maybe it's because there is no way to run a script between user switches?  I don't know. 

In all events, their is a much better solution to the underlying problem that I was trying to address:  switch the super and control keys so that I can use a Mac layout keyboard and have the Mac "command" button be equivalent to the Ubuntu "control" button.  I was using an old method: xmodmap.  The current method uses xkb.  

[Here]("http://askubuntu.com/questions/501659/how-to-swap-command-and-control-keys-with-xkb-step-by-step") is the way to do it.  This is persistent across user switches and requires no scripts.

---

### Post by xmbwd on 2014-11-14
DAMN!  I thought it worked.  But on restart, it's gone and the CTRL and SUPER are back to their original spots.  

Does anyone -- anyone! -- know how to make the xkb setting persistent so that I can switch two very simple keys???  Please . . . . this is driving me crazy.

---

