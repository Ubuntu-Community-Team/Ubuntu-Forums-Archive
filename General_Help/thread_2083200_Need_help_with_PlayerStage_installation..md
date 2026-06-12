---
title: "Need help with Player/Stage installation."
date: 2012-11-11
forum: General Help
---

### Post by naruki on 2012-11-11
I'm trying to install Player/Stage on 12.04 32-bit. I'm following:

[http://www.cnblogs.com/kevinGuo/archive/2012/05/03/2480077.html](http://www.cnblogs.com/kevinGuo/archive/2012/05/03/2480077.html)

I managed to install it but when I tested it, I got the error predicted by the author of the manual:
```

Registering driver Player v.3.0.2
* Part of the Player/Stage/Gazebo Project [http://playerstage.sourceforge.net]. 
* Copyright (C) 2000 - 2009 Brian Gerkey, Richard Vaughan, Andrew Howard, 
* Nate Koenig, and contributors. Released under the GNU General Public License.
* Player comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it under certain conditions; see COPYING for details.

error : Failed to load plugin stageplugin. 
error : libtool reports error: file not found
error : plugin search path: /home/robotlab/playerstage/Stage-3.2.2-Source/worlds:.:/usr/local/lib/
error : failed to load plugin: stageplugin error : failed to parse config file simple.cfg driver blocks
```Okay so, the author's solution is > This is most likely caused by the computer not being able to find Stage. Back to the .bashrc....
 
[LIST]
[*]
[LIST]
[*]change export LD_LIBRARY_PATH+=/usr/local/lib64 to...
[*]export LD_LIBRARY_PATH+=/usr/local/lib64:/usr/local/lib
[/LIST]
 
[/LIST]
I'm assuming that for my case, it should be "/usr/local/lib:/usr/local/lib" since I'm using the 32-bit system.  The end of my ./bashrc file looks like: 

```

..........
..........
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

export LD_LIBRARY_PATH+=/usr/local/lib:/usr/local/lib

```

But I'm still getting the same error. I don't know how to diagnose this.

---

