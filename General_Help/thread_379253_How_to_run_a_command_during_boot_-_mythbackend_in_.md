---
title: "How to run a command during boot? - mythbackend in this case"
date: 2007-03-08
forum: General Help
---

### Post by viciouslime on 2007-03-08
What is the "correct" way to make something run at startup. Things like apache seem to do this automatically when you install the package, but other things, like mythtv, do not. How should I go about making mythbackend, or any other similar process for that matter, start when ubuntu is booting?

Thanks :)

---

### Post by Del Boy on 2007-03-08
Put your script in /etc/init.d/ and then make it executable by running ```
chmod +x script
```  and then run ```
update-rc.d script defaults
```

---

### Post by viciouslime on 2007-03-08
Thanks for your help, I tried creating a script as follows:
```
#!/bin/bash
mythbackend
```

I then ran ```
sudo update-rc.d mythbackend defaults

``` which appeared to work, but on restart, mythbackend is not running :(

---

### Post by yopnono on 2007-03-08
> **viciouslime said:**
> Thanks for your help, I tried creating a script as follows:
```
#!/bin/bash
mythbackend
```

I then ran ```
sudo update-rc.d mythbackend defaults

``` which appeared to work, but on restart, mythbackend is not running :(

mythbackend need to be in the path like /usr/bin or use the full path to it /your/path/mythbackend

Also the script need to be executable

---

### Post by AZzKikR on 2007-03-08
What I usually do (whether it is a good method or not) is first creating a script in the directory (in your case)
```
/etc/init.d/mythbackend
```
In this file, I'd create something like this:
```

#!/bin/bash
# define some variables or whatever you need

case in
    start)
        # code to start the mythbackend
        ;;
    stop)
        # code to stop the mythbackend
        ;;
    *)
        # inform the user that the script must be called using /etc/init.d/mythbackend start|stop
        ;;
esac

```
I do not remember the syntax of this correctly since I am on a Windows box at the moment, but if you look at some scripts in the /etc/init.d/ directory, you can probably see some examples. If your script is made, make it executable:
```

$ sudo chmod +x /etc/init.d/mythbackend
```

Now, take a look at the directory:
```
/etc/rc2.d/
```
This directory contains symbolic links to applications which are started at boot. As you can see, they all point to the /etc/init.d/ directory. The higher the number given, the later it is started in the sequence.

If you'd like to pursue this way of creating a startup script, let me know, I'll give more detailed information when I am at home :)

---

### Post by majoridiot on 2007-03-14
mythbackend should start by itself at boot...

the init script itself is /etc/init.d/mythtv-backend

using start stop or restart

it is run at startup by a symbolic link- /etc/rc5.d/S24mythtv-backend  which points to the above init script.

if your backend server isn't starting by itself, check those two things.

---

