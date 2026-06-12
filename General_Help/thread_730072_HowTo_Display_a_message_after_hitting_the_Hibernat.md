---
title: "HowTo: Display a message after hitting the Hibernate button"
date: 2008-03-20
forum: General Help
---

### Post by mydexterid on 2008-03-20
Hey there!

I'm using Ubuntu Gutsy, and I wanted to display some message right after I hit the Hibernate button, but before the actual hibernate takes place. Notice! I'm not really aware of bash scripting, and this method is a really dirty hack, but it works.. at least for me :) So here is how to do that:

1.  Open gconf-editor. Go to Apps->gnome-power-manager->lock
    uncheck hibernate. This will inhibit powermanager to lock your screen right after you click the hibernate button.

2. edit file: /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
  This is what you have to add to this script (for the sake of simplicity let's say add this right after the first line "#!/bin/sh"):
```

getXuser() {                                                                                                                                                 
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`                                                                                           
        if [ x"$user" = x"" ]; then                                                                                                                          
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`                                                                                    
        fi                                                                                                                                                   
        if [ x"$user" != x"" ]; then                                                                                                                         
                userhome=`getent passwd $user | cut -d: -f6`                                                                                                 
                export XAUTHORITY=$userhome/.Xauthority                                                                                                      
        else                                                                                                                                                 
                export XAUTHORITY=""                                                                                                                         
        fi                                                                                                                                                   
}                                                                                                                                                            
                                                                                                                                                             
        for x in /tmp/.X11-unix/*; do                                                                                                                        
            displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`                                                                                                  
            getXuser;                                                                                                                                        
            if [ x"$XAUTHORITY" != x"" ]; then                                                                                                               
                export DISPLAY=":$displaynum"                                                                                                                                                                                                                                
                 pid=`pgrep -u USERNAME gnome-screensav`                                                                                                       
                 DBUS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`                                                                                                                                            
                ###HERE RUN ANY PROGRAM WHICH WILL DISPLAY YOUR MESSAGE ###
                DBUS_SESSION_BUS_ADDRESS="$DBUS" su -c "/usr/bin/gnome-screensaver-command -a" USERNAME                                                        
             fi                                                                                                                                               
        done

```

Replace USERNAME with your X username. So in this way you can run any script/program (actually I wrote a simple GTK app which displays my message) before it goes on hibernating. After we ran our app, we're invoking the gnome-screensaver so in this way when you resume your work, it'll ask for your password first.

**I would really appritiate if someone could tell me how to do this with the Shutdown button.**
I already tried hal-system-power-shutdown-linux but as I noticed this is not the one what gets executed when I hit the Shutdown button.

---

### Post by bhavi on 2008-03-21
> **mydexterid said:**
> Hey there!

I'm using Ubuntu Gutsy, and I wanted to display some message right after I hit the Hibernate button, but before the actual hibernate takes place. Notice! I'm not really aware of bash scripting, and this method is a really dirty hack, but it works.. at least for me :) So here is how to do that:

1.  Open gconf-editor. Go to Apps->gnome-power-manager->lock
    uncheck hibernate. This will inhibit powermanager to lock your screen right after you click the hibernate button.

2. edit file: /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
  This is what you have to add to this script (for the sake of simplicity let's say add this right after the first line "#!/bin/sh"):
```

getXuser() {                                                                                                                                                 
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`                                                                                           
        if [ x"$user" = x"" ]; then                                                                                                                          
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`                                                                                    
        fi                                                                                                                                                   
        if [ x"$user" != x"" ]; then                                                                                                                         
                userhome=`getent passwd $user | cut -d: -f6`                                                                                                 
                export XAUTHORITY=$userhome/.Xauthority                                                                                                      
        else                                                                                                                                                 
                export XAUTHORITY=""                                                                                                                         
        fi                                                                                                                                                   
}                                                                                                                                                            
                                                                                                                                                             
        for x in /tmp/.X11-unix/*; do                                                                                                                        
            displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`                                                                                                  
            getXuser;                                                                                                                                        
            if [ x"$XAUTHORITY" != x"" ]; then                                                                                                               
                export DISPLAY=":$displaynum"                                                                                                                                                                                                                                
                 pid=`pgrep -u USERNAME gnome-screensav`                                                                                                       
                 DBUS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`                                                                                                                                            
                ###HERE RUN ANY PROGRAM WHICH WILL DISPLAY YOUR MESSAGE ###
                DBUS_SESSION_BUS_ADDRESS="$DBUS" su -c "/usr/bin/gnome-screensaver-command -a" USERNAME                                                        
             fi                                                                                                                                               
        done

```

Replace USERNAME with your X username. So in this way you can run any script/program (actually I wrote a simple GTK app which displays my message) before it goes on hibernating. After we ran our app, we're invoking the gnome-screensaver so in this way when you resume your work, it'll ask for your password first.

**I would really appritiate if someone could tell me how to do this with the Shutdown button.**
I already tried hal-system-power-shutdown-linux but as I noticed this is not the one what gets executed when I hit the Shutdown button.
Nice trick mate..... Tried it out now... Thanks.......

---

### Post by mydexterid on 2008-03-21
You're welcome ;)

---

