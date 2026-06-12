---
title: "Remote desktop, alter default listening port?"
date: 2005-04-14
forum: General Help
---

### Post by fxer on 2005-04-14
I've checked around the forums but haven't found a way to change the remote desktop session listening port in Hoary from 5900 to 5901 or something else, my new Ubuntu machine is behind a router and port 5900 is already being forwarded in the router to another vnc install.

Also should get Firestarter and setup a firewall if I'm going to open the remote desktop port?

Wow, Ubuntu is great so far, thanks for the help!

---

### Post by fxer on 2005-04-14
I see information about using SSH tunneling to forward port 5900 to 5901 locally, but I don't really need to encrypt the communication for what I'm doing...

---

### Post by speedman on 2005-04-14
You may want to run the vanilla vncserver, which is in the Ubuntu repositories instead of vino.  I just had a quick look at the source code for vino-server at it looks like the default behaviour for vino is to start probing for a non occupied port beginning at 5900 and ending at 6000 without any runtime options being configurable.

This would be the applicable porition of code from vino-server.c:

   *   setting autoPort enables autoProbing a port between
   *   5900-6000
   */
  rfb_screen->rfbDeferUpdateTime = 0;
  rfb_screen->autoPort           = TRUE;

HTH


Regards,

SM

---

### Post by fxer on 2005-04-15
Thanks for snooping around in the code, no one seemed to have an answer for this one! Do you think it may be possible to alter the AutoPort method to just start scanning at 5001-6000 or something? 

Not sure I want to go to that trouble though when i can just install a package in Synaptic to do what I want. it'd be nice to be able to control it through the Ubuntu remote desktop control panel just for some extra convenience though. Perhaps I should put the option in as a feature request :)

---

### Post by speedman on 2005-04-15
> **fxer]Thanks for snooping around in the code,[/QUOTE]

No problem.

> no one seemed to have an answer for this one!

I'm starting to discover why that is.  :) 

> Do you think it may be possible to alter the AutoPort method to just start scanning at 5001-6000 or something?

It appears that vino builds against libvncserver (which is one of many vnc implementations) and the source that is included for libvncserver with the vino source is also hard coded to port 5900.

Here are the specific code segments that are hard coded in the vino source tree:

chris@i8500:~/Desktop/vino-2.10.0/server $ grep -r 5900 *
libvncserver/main.c:   rfbScreen->rfbPort=5900 said:**
> Not sure I want to go to that trouble though when i can just install a package in Synaptic to do what I want.

I suppose there is a caveat that I should have mentioned previously with regards to vncserver.  Unlike vino (and x0rfb) vncserver spawns a new desktop instance when remote connections are made.  In other words it does not allow a remote connection to your existing desktop session (such as vino), which may be pertinent to your decision.

> it'd be nice to be able to control it through the Ubuntu remote desktop control panel just for some extra convenience though.

Indeed.

> Perhaps I should put the option in as a feature request :)

I agree it would be a nice feature, but the request should go upstream.  Ubuntu and Debian developers would most likely feel the changes are too much of a divergence from the original code base to implement themselves - not because it is too much work, but more so because it would deviate beyond what is considered appropriate for a package maintainer to undertake.

[email]desktop-devel-list@gnome.org[/email] is the relevant mailing list:

[http://mail.gnome.org/mailman/listinfo/desktop-devel-list](http://mail.gnome.org/mailman/listinfo/desktop-devel-list)

In the interim perhaps a wrapper script implementing a local SSH port forward (as you mentioned earlier) in conjunction with loading vino-server might be the best option.

Clear as mud?  :) 


Regards,

SM

---

### Post by fxer on 2005-04-16
Thanks again for all the help, I subscribed to and posted a message to (referencing this thread) the gnome-desktop-devel list, we'll see what they say :)

 For the moment i've just been vnc-ing into my winxp box behind the router, then from there getting into the ubuntu install on another machine by directly referencing its IP behind the router. So it's not the most efficient way on earth, but it works :) 

Hopefully the developers of gnome would agree with my suggestion of an "advanced" button or tab or something that would enable binding to a port of the users choosing. I see it as more useful than frivilous but we'll see! It is times like these I wish I was a better coder :) Thanks again!

---

### Post by speedman on 2005-04-17
[QUOTE=fxer]For the moment i've just been vnc-ing into my winxp box behind the router, then from there getting into the ubuntu install on another machine by directly referencing its IP behind the router. So it's not the most efficient way on earth, but it works :) [/QUOTE]

How about just doing a port forward off your router?  Depending on the router you should be able to forward incoming requests on a non standard port, such as 6900 to be forwarded to port 5900 on your Ubuntu system.


Regards,

SM

---

### Post by ionos on 2005-04-17
From  my xorg.conf file:

```

Section "Device"
  BoardName    "Radeon LW"
  Option       "rfbauth" "/path/to/vnc/passwd/file"
  Option       "rfbport" "5555"
  Option       "usevnc" "yes"
  ...
EndSection

```

Cheers
 - i

---

### Post by speedman on 2005-04-17
Nice tip ionos.  I just did a bit of reading and it appears that you also need a:

Load "vnc"

... line in xorg.conf and that the applicable vnc server is vnc4server.

=====

chris@i8500:~ $ apt-cache show vnc4server

<SNIP>

It contains an X server connector so clients can connect to your local X
desktop directly.

=====

More information is available here fxer if you're interested:

[http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=xorg.conf+rfb+vnc](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=xorg.conf+rfb+vnc)


Regards,

SM

---

### Post by ionos on 2005-04-17
[QUOTE=speedman]Nice tip ionos.  I just did a bit of reading and it appears that you also need a:

Load "vnc"
[/QUOTE]

Yes, of course. I took that for granted ;-)

Cheerio,
 - i

---

### Post by arsenik on 2006-04-21
I've been searching for a way to change the port also. However I don't really understand what you guys are talking about here.. can someone put it in newb terms for me?

---

### Post by stanna on 2006-05-02
god knows why this is such a hassle. i dont have the option to forward one port to another on my router. i have looked at as much documentation and conf files as i can find and yet still dont have a solution to how to change the default port for vnc4server under ubuntu 5.10

i searched around and found this [post]("http://leovilletownsquare.com/fusionbb/showpost.php?post/26489/"). looked like it might help.

so i searched /usr/bin/vncserver for 5900 and changed it to the new port i wanted to use. lets hope it works. i wont have a chance to test it out until the weekend.. but it might work. ill come back and post if it works or not soon.. i hope it helps other.

---

### Post by stanna on 2006-05-08
[QUOTE=stanna]god knows why this is such a hassle. i dont have the option to forward one port to another on my router. i have looked at as much documentation and conf files as i can find and yet still dont have a solution to how to change the default port for vnc4server under ubuntu 5.10

i searched around and found this [post]("http://leovilletownsquare.com/fusionbb/showpost.php?post/26489/"). looked like it might help.

so i searched /usr/bin/vncserver for 5900 and changed it to the new port i wanted to use. lets hope it works. i wont have a chance to test it out until the weekend.. but it might work. ill come back and post if it works or not soon.. i hope it helps other.[/QUOTE]

[QUOTE=arsenik]I've been searching for a way to change the port also. However I don't really understand what you guys are talking about here.. can someone put it in newb terms for me?[/QUOTE]


it did not work for me.

---

