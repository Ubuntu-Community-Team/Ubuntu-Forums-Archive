---
title: "How to force Lenovo thinkpad to see external monitor at login"
date: 2014-09-26
forum: General Help
---

### Post by stevecook on 2014-09-26
Hello folks.

I've been having problems with my Lenovo thinkpad not picking up my television which I am using as an external monitor. After much reading on the internet finding that this was a common problem for others (not just with the Lenovo Thinkpad) and after also finding nothing on the internet that worked, I came up with the following solution that certainly works for my setup. I should say, I am using Ubuntu 12.04 LTS with Gnome.

As a preamble, I need to spell out the problem I was having in more detail so you can see if it matches yours;

My preferred resolution on the Lenovo Thinkpad's integrated monitor is 1024 by 768, whereas my preferred resolution on the television is 800 by 600. The reason being, I am using my external monitor as a television in my lounge to view things like iplayer, youtube, itvplayer, 4od etc in fullscreen. This means I need a much lower resolution on my external monitor so I can I see text/menus ect from across the room. These two different resolutions, it turned out, were the problem. If I set the two different resolutions from the Display Settings manager whilst in Ubuntu, it initially (at least for the remainder of that session) all worked fine. I would also set the laptop monitor as "off" in the Display Settings manager so that only my TV monitor was displaying anything. The problem arose the next time I booted up and logged in. At bootup and the login screen itself, both monitors would display. So far so good (notwithstanding the fact that I only wanted the external monitor to display anything). However, as soon as I actually logged in, both displays would then go blank. The only way to fix this, initially, was to physically unplug the VGA cable to the external monitor and then plug it back in. At which point, the laptop monitor would switch off as it should and the external monitor would switch on. This, though, was a very sloppy solution and so unsatisfactory. 

I then played around with different display settings and found that if both settings were set to 1024 by 768 (which was my preferred laptop integrated display setting) then everything worked as it should. That is to say, the next time I logged in, the TV monitor would come on and the laptop monitor would stay off. That being the case, it occured to me that the problem was that my Lenovo Thinkpad could not detect my TV monitor when set at 800 by 600 at login. But, *could* detect it if that resolution was selected **after** login. Thus, the solution was to write up a little bash script to run at startup that would, initially, set the resolution to 1024 by 768 and then immediately re-set it to 800 by 600. Voila, it worked! Obviously, anybody else may need to play around with their own display settings to see which resolution will allow for both monitors to be detected immediately following logon including finding out which two *different* resolutions (if you want different resolutions like I did) can be obtained by setting them in the Display Manager whilst in a Desktop session. Once you have all of the above information under your belt you can implement the following solution:

1) In the Display Manager (you will find this in "system settings" under "system-tools" on your menu ), set the resolution you want and/or works for your integrated laptop monitor.

2) In the Display Manager, set the resolution you want and/or works on your external monitor.

3) In the Display Manager, set the "mirror displays" option to "off".

4) In the display Manager, set the laptop monitor to "off". You should now only see a display on your external monitor. Now close the Display Manager.

5) Open up simple text editor like "geddit". This can be found on your accessories menu or, in Unity, by typing geddit in the dash . I should say, though, any simple text editor will do.

6) Copy the following commands into the text editor. Though, remember to change the actual resolution settings to those you want them to be.

[B]xrandr -s 1024x768
xrandr -s 800x600[/B]

What this command is doing is telling the system to send 1024 by 768 to the  external monitor (because this is, in my case, what the laptop is using for its own screen, so we know that this resolution will work on the external monitor no matter what). However, immediately after, the second command then reverts to the display settings that are *actually* wanted on the external monitor, Namely, (in my case) 800 by 600. Because this has been done *after* setting the initial display settings that the laptop "preferred", it will now accept the new settings of 800 by 600.

7) Save the file as:

**set-res.sh**

It will automatically save to your home folder. Which is where you are in your terminal when you first open it as it happens. If you type "ls" now you will see it listed as one of the files. What you need to do now is to make it executable.

8) Type the following to make the file executable:
 
 **chmod +x set-res.sh**

You can close the terminal now.

This script will need to be automatically run each time you start Ubuntu to make your external monitor work at login

9) Using your menu, go to something called “Startup Applications”, In the  classic Gnome interface, this is under tools. In the Unity interface, I  would think it will come up if you type it into the search box on the  dash. It looks like this:

[[IMG]http://i958.photobucket.com/albums/ae67/stevecook172001/startup1.png[/IMG]]("http://s958.photobucket.com/user/stevecook172001/media/startup1.png.html")

10) Click on the “Add” button:

[IMG]http://i958.photobucket.com/albums/ae67/stevecook172001/startup2.png[/IMG]

11) For the Command, press the "browse" button and navigate to your  “set-res.sh” file and choose it (it's in your home folder, remember). For the Description, simply write  "set resolution" (or whatever you want) in the box.

12) Close the “add” dialogue box. You should now see this file listed as one  of your start-up applications in the start-up-applications dialogue  box. Close the start-up-applications dialogue box.

That's it. From now on, every time you start Ubuntu 12.04 LTS, this file  will will run automatically and hopefully your external monitor should work immediately following login.

My guess is, this fix will probably work for any version of Ubuntu and any model of computer that is refusing to see the external monitor at login for the reasons I have described (though there may, of course, be other reasons), That is just a guess, though, and I would appreciate feedback to see how this solution went for other people.

---

