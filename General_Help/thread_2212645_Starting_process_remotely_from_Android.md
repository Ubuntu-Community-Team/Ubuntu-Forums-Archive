---
title: "Starting process remotely from Android"
date: 2014-03-22
forum: General Help
---

### Post by LinuxUser666 on 2014-03-22
Greeting fellow Ubuntu users I'm running Xubuntu 12.10 with OpenSSH client and server installed and I've got 2 Android devices powered by Cyanogenmod 10 with ConnectBot [https://play.google.com/store/apps/details?id=org.connectbot](https://play.google.com/store/apps/details?id=org.connectbot) installed as my ssh client on them. My question is how can I use my Android devices to start a service or process, just start them, I do not need any graphical outputs on my device, just start the service. For instance I've tried to start Clementine player on my Xubuntu machine from Android with just this command: ```
clementine
``` and it gave me this output ```
clementine:cannot connect to X server
``` So Please tell me how to start my Clementine and/or any other service/process without getting this error.

Many regards, Stay brutal.

---

### Post by TheFu on 2014-03-22
Clementine is a GUI program. It cannot be started without an X/Server attached.  If the programmers didn't link any GUI libraries for the non-GUI part of the program, then you would be able to start it has a service.

It is possible to trick a service into believing there is an X/Server available using an **xvfb**.  A slight understanding of X/Windows will be needed to get that working.  This is commonly used on pure UNIX servers since a few Oracle products require X/Windows to run ... on pure servers. Idiots. Anyway, that should get you started.

---

### Post by Lars Noodén on 2014-03-22
If you have a grapical program that you want to display on the remote desktop, you can inform it manually of the $DISPLAY.

```

DISPLAY=:0.0 clementine

```

That way it will both run and display on the remote system, assuming it is a desktop with X and everything.

---

### Post by TheFu on 2014-03-22
> **Lars Noodén said:**
> If you have a grapical program that you want to display on the remote desktop, you can inform it manually of the $DISPLAY.

```

DISPLAY=:0.0 clementine

```

That way it will both run and display on the remote system, assuming it is a desktop with X and everything.

Is there an X/server for Android?!!!!  That would be great!

---

### Post by Lars Noodén on 2014-03-22
That will display it on the system he has logged into, not the Android system he is logging in from.  But he will be able to launch it remotely. 

I don't have Android to play with but there seem to be several things claiming to be X servers in Google Play.

---

### Post by TheFu on 2014-03-22
If setting DISPLAY=:0 works, it is a bug in the X-auth.  That shouldn't be allowed without a few more steps especially if there isn't a console user on the remote machine. If the existing remote user is a different userid, and there's something else required - can't recall it now.

BTW, I like clementine, but the C/S aspects are flaky.

---

### Post by LinuxUser666 on 2014-03-23
Many thanks to you all, I haven't tried ```
DISPLAY=:0
``` because TheFu's method worked with ```
clementine -xvfb
``` actually almost correct it's ```
clementine -vfb
``` because it returned invalid argument in 1st command, many thanks to you all, I'm much obliged, stay brutal. :D

---

### Post by TheFu on 2014-03-23
I would be surprised if that worked.
Running the xvfb is needed first, set the DISPLAY for that virtual-device and set the DISPLAY for just clementine to use.

---

### Post by Lars Noodén on 2014-03-23
> **TheFu said:**
> I would be surprised if that worked.

It would only work if there is already an X server on that machine and the same user is already logged in.

---

### Post by LinuxUser666 on 2014-03-23
Well my man, it worked...I opened Clementine player from ConnectBot app without it returning me any kind of error and now my Clementine is running so...yeah it did the trick, all I asked for. 

My regards, stay brutal. And yeah I had NO need for DISPLAY so far...Idk why it surprised you, but oh well I'm sure you have your reason :D but anyway thanks, you helped a lot.

---

### Post by LinuxUser666 on 2014-03-23
> [COLOR=#000000]It would only work if there is already an X server on that machine and the same user is already logged in.[/COLOR] Well yeah that's why it worked, I have an established working GUI and me as user logged in :D 

My regards, stay brutal.

---

### Post by TheFu on 2014-03-23
> **Lars Noodén said:**
> It would only work if there is already an X server on that machine and the same user is already logged in.

Agreed. Or there is a HUGE security flaw in the X/Windows running on his box.

So ... did some more work on this.
**xvfb-run clementine** is the command that works as a server for the Clementine-Android client - provided the network remote control is enabled inside the preferences.
What this does is start a clementine server that can be controlled by a network client. Audio playback still happens though the server audio card/connections.  Great for a HTPC connected to a stereo already.

---

