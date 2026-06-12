---
title: "How to add user name or UID to a file name from a command?"
date: 2019-12-17
forum: General Help
---

### Post by GhX6GZMB on 2019-12-17
I'd like to add a "static" variable to a file name in a user command.

The command is:

 **scrot -o /tmp/clip.png**

Instead of **clip.png**, I'd like it to be **clip_"username".png** or **clip_UID.png** instead.

I'm aware of the time/date append option, but this will not solve my issue.

So how do I insert this into the file name? echo? whoami? id? I've found several ways of getting the info, but using it to create a file name eludes me.

Thank You.

---

### Post by yetimon_64 on 2019-12-17
The first thing I have noted when looking into this is there is no "-o" option with scrot...
```
yetiman:~ $  scrot -o /tmp/clip.png
scrot: invalid option -- 'o'
```

But getting back to your idea of inserting your username into a saved file with scrot I chose one of my scrot commands to save the active window which goes like ...
```
scrot -b -u -m -d1 ~/Screenshots/scrot-active_%H:%M:%S_%d-%b-%Y.png
```
This command saves the active window and when run in terminal saves an image of the terminal with the date included in the filename. An example of the name outputted from the above command is "scrot-active_09:02:53_18-Dec-2019.png".

Now to add my username to the above command between "scrot-active" and the date I used....
```
scrot -b -u -m -d1 ~/Screenshots/scrot-active_$(whoami)_%H:%M:%S_%d-%b-%Y.png
```
Filename example .... "scrot-active_yetiman_09:07:50_18-Dec-2019.png".

For the userid instead of "$(whoami)" you can use "$(id -u)"...
```
scrot -b -u -m -d1 ~/Screenshots/scrot-active_$(id -u)_%H:%M:%S_%d-%b-%Y.png
```
 Filename example .... "scrot-active_1000_09:17:56_18-Dec-2019.png".

So in summary to add the username insert...
```
$(whoami)
```
... and to add the userid insert ...
```
$(id -u)
```
...into the filename part of the scrot command.

If you wish to see what my command options are doing run the command "man scrot" and look under the "OPTIONS" section.

Regards, yeti.

---

### Post by GhX6GZMB on 2019-12-18
@ yeti:
pure gold, Thank You, Thank You, Thank You.

CLI **scrot -o /tmp/clip_$(id -u).png** works exactly as expected and creates **/tmp/clip_1000.png** as I wished.

The -o option is "overwrite" and specified in man scrot. Perhaps we have different versions?

I now face a different problem. CLI works, but assigning the command to a Shortcut Key in LXQt does not work... a mystery, I'm investigating.

Thank You again.

---

### Post by yetimon_64 on 2019-12-18
> **ml9104 said:**
> ...The -o option is "overwrite" and specified in man scrot. Perhaps we have different versions?...

I'd say you are right there about the versions being different. No sign of that option with "man scrot" here. I am on Ubuntu Mate 18.04 btw.

Not sure about your problem with the shortcut on LXQT. Await further advice from other helpers using LXQT for that, though it may help you to add tags to your question or title to specify LXQT is in use.

Regards, yeti.

---

### Post by GhX6GZMB on 2019-12-18
OK, problem fixed.

After experimenting a bit, it turns out the the "Shortcut Keys" in LXQt is not able to expand a command, so $(id -u) is not evaluated at all.

My solution is a one-line script in /home (called screenshot_scriptfs.sh , permissions 777) containing:

scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard  -t image/png < $f'

The shortcut key now has the assignment "sh /home/screenshot_scriptfs.sh"

Works wonderfully and works for all users.

Thank You again. (I'm on Lubuntu 19.10)

---

### Post by TheFu on 2019-12-18
There are also environment variables with that information which would be more efficient. No need to spawn a new process.
```
$ env
....
USER=thefu
LOGNAME=thefu
...
```

USER seems to be set only with a user session - i.e. not under cron.
LOGNAME seems to be set based on the effective-uid for a process.

---

### Post by Impavidus on 2019-12-19
> **ml9104 said:**
> 
My solution is a one-line script in /home (called screenshot_scriptfs.sh , permissions 777) containing:


Don't use permissions 777. This means that every user not only has permission to read and execute the script, but also to modify it. So every user can add lines to the script, for example to plant malware in the invoking user's home directory. Set permissions to 755 instead.

---

### Post by GhX6GZMB on 2019-12-19
> **Impavidus said:**
> Don't use permissions 777. This means that every user not only has permission to read and execute the script, but also to modify it. So every user can add lines to the script, for example to plant malware in the invoking user's home directory. Set permissions to 755 instead.

Good point, done. I only set 777 for testing to be certain that permissions wouldn't interfere.

---

### Post by GhX6GZMB on 2019-12-19
> **TheFu said:**
> There are also environment variables with that information which would be more efficient. No need to spawn a new process.
```
$ env
....
USER=thefu
LOGNAME=thefu
...
```

USER seems to be set only with a user session - i.e. not under cron.
LOGNAME seems to be set based on the effective-uid for a process.

TheFu, Thank You, I know that my solution is probably not the most elegant, but I'm still an amateur :)

But I have a solution that works reliably, which makes me happy.

---

