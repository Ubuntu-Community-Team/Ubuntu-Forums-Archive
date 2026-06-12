---
title: "Terminal command to prevent a system from going into suspend mode?"
date: 2014-03-07
forum: General Help
---

### Post by Roasted on 2014-03-07
Hello friends. Here's the scoop. I work for a school district with a few thousand Ubuntu 12.04 LTS machines. They're all laptops. Every so often I'll clusterssh into a bunch of them to run updates/dist-upgrades. Clusterssh allows me to basically issue 1 command and have it auto-replicate to 5, 10, 30, 60, whatever other SSH windows that are associated with that cluster. Thing is, these are laptops, and they go into an auto-suspend mode often times before some of these larger dist-upgrades can complete. 

So what I'm curious about is whether or not there's a way to issue a command in terminal over SSH to all of these machines at the beginning of my session, thereby lifting the auto-suspend timer entirely until next reboot. Then I can let these machines run for hours without paying attention to them, come back, and reboot them to finish things out.

As mentioned, I don't want this to be permanent. Just something to temporarily lift it for that session. Is such a thing possible?

---

### Post by tomearp on 2014-03-08
From [looking around]("http://askubuntu.com/questions/71972/how-do-i-inhibit-suspend-from-the-command-line") it looks like one of the simplest ways is to use xdotool to generate keyboard button presses.

```
sudo apt-get install xdotool
```
then use a simple bash script to repeatedly 'press' a key
```
while true ; do
    DISPLAY=:0.0 xdotool key Shift_L
    sleep 5
done
```

As you're controlling lots of machines you could log the pid somewhere to make it easy to kill when done.

E.g.:
```
/some/directory/yourscript &
```
to run the script in the background, then
```
echo $! > /var/run/yourscript.pid
```

Now you have a pid file to kill it is easy
```
kill -kill `cat /var/run/yourscript.pid` && rm /var/run/yourscript.pid
```

---

### Post by TheFu on 2014-03-08
I did about 30 minutes of research and didn't find an easy answer.  It appears that modifying the policy is the only way - a text file on each box. [http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate](http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate)

So ... I've used clusterssh for about a decade. The main weakness I've had with it was editing files. There are other tools to manage lots of systems - you've probably heard of puppet and chef. IMHO, these are overly complicated to get setup before the first management can begin.  A former Puppet Labs employee thought the same thing and created **Ansible**.  Might be worth a look.  Your client machines already have the required dependencies.  Took me about 30 minutes to start managing a box and 5 more minutes to start managing 30 machines. [Quick Start video.]("http://docs.ansible.com/quickstart.html")  I don't have 2K systems to manage, but Ansible has really helped with our 30 systems.

Coming at this from a different angle - if you don't have an apt-cache setup, perhaps that could reduce the time to deploy by avoiding the WAN downloads for almost all updates.  We use apt-cacheng.

None of these tools is perfect.  Anyway, hope this helps.

-- Update --
This question really got me thinking and searching ... THANKS!
[http://askubuntu.com/questions/170307/how-does-ubuntu-determine-inactivity-before-suspending](http://askubuntu.com/questions/170307/how-does-ubuntu-determine-inactivity-before-suspending) says that how busy a system is doesn't matter at all. It is only GUI events that determine if the system is considered idle or not. That sorta sucks. Anyway, if that truly is the case, then the **xset** command should be a way to change the GUI timeout. But xset does NOT exist on pure servers (no X/Windows).
I searched inside every file on my main desktop (runs LXDE on 12.04 Server) for org.gnome.SessionManager.Presence.status and nothing was found, so the way spelled out in that link is NOT guaranteed to work.

Like tomearp suggests, toggling a keyboard might be the easiest way to accomplish this if a way to increase the GUI timeout can't be determined. If an update takes more than 45 minutes, I'd think something is wrong enough to need personal attention. 

This question is going to drive me nuts. ;) Can't wait to learn how you solved it!

---

