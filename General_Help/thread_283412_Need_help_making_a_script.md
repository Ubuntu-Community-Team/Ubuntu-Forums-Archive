---
title: "Need help making a script"
date: 2006-10-24
forum: General Help
---

### Post by bluenova on 2006-10-24
Hello all,

I need some help to make a very simple script, but I have no idea how to do it.

What I need to do is something like this:

```
IF [color=blue]"a user is logged on"[/color]
THEN ECHO "A user is still logged on"
ELSE sudo shutdown -h now
```

How can I get it to find out if a user is still logged on?

Then reason behind it, I only want people to be able to shut down from the GDM screen if no other users are logged on. I will change /sbin/gdm.conf greeter section to point to the new script rather than shutdown -h now.

Thanks for your help.

---

### Post by kidders on 2006-10-24
Hi there,

You could try something like this maybe...

```

#/bin/sh

ME=`whoami`

for i in `w -h | sed 's/\s.*//'`; do
	if [ "$i" != "$ME" ]; then
		echo "$i is still logged in :-(";
		exit 1
	fi
done

echo "Enter your password to shut down"
sudo shutdown -h now

```

You'd have to tweak it slightly to get it to run through GDM, but the idea would be the same. My example checks for logins that are not yours, before shutting down.

Hope that helps.

---

### Post by bluenova on 2006-10-24
Loggins that are not yours would work as well, then the user can just try and shutdown from their area. The reason for the GDM was that they can then see 'User logged in' next to the user name, using the greeter I have. I'll give it a try, thanks!

---

### Post by bluenova on 2006-10-24
It works well, thank you!

Only thing is, how can I get it to echo in a GUI window? I think there is an option instead of echo but I can't remember it.

::EDIT::
Found it, it was zenity.

---

### Post by bluenova on 2006-10-24
Ok, needs some help again. So I now have this:

```
#/bin/sh

ME=`whoami`

for i in `w -h | sed 's/\s.*//'`; do
	if [ "$i" != "$ME" ]; then
		zenity --error --title="Shutdown the computer" --text="I'm sorry but you cannot shutdown now, $i is still logged in and may be using the computer";
		exit 1
	fi
done

zenity --question --title="Shutdown the Computer" --text="Yey! All users are logged off, are you sure you want to shutdown?" "/sbin/shutdown -h now"
```

I have also added to sudoers:
*username localhost= NOPASSWD: /sbin/shutdown -h now*
So that the non-sudoer users can also shutdown.

So the problem is now that when zenity pops up it's box to ask if it's ok to shutdown nothing happens after that. man zenity tells me that zenity will report a 0 for ok and a 1 for cancel, so does that mean I have to say something like If 0 then shutdown -h now? I tried a few things but none of them worked.

---

### Post by IYY on 2006-10-24
I've never used zenity, but if you want a process to execute if a previous process finished executing successfuly, you can use "&&". So, 

zenity --question --title="Shutdown the Computer" --text="Yey! All users are logged off, are you sure you want to shutdown?" && "/sbin/shutdown -h now"

---

### Post by skymt on 2006-10-24
> **IYY said:**
> I've never used zenity, but if you want a process to execute if a previous process finished executing successfuly, you can use "&&". So, 

zenity --question --title="Shutdown the Computer" --text="Yey! All users are logged off, are you sure you want to shutdown?" && "/sbin/shutdown -h now"

Or, if you want something that looks a bit nicer:```
if zenity --question --title="Shutdown the Computer" --text="Yey! All users are logged off, are you sure you want to shutdown?" ; then
    /sbin/shutdown -h now
fi
```

---

### Post by bluenova on 2006-10-25
Worked great thanks! My users can only shutdown now as long as nobody else is logged on.

---

