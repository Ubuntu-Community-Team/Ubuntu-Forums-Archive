---
title: "XDMCP/GDM Problems"
date: 2005-05-05
forum: General Help
---

### Post by rmmcgr on 2005-05-05
Hi,

After I login to my Ubuntu machine, via XDMCP accessed on my Windows box (thanks to Cygwin) all I get is a blank, brown, screen.

I don't have any firewall running on the Ubuntu box, as far as I know (unless one is installed by default).  But I don't see how that would be a problem anyways as I am able to bring up the GDM login screen.

What is the trick to get this working.  I am using 5.04 version of Ubuntu.

Thanks for any help,
Richard

---

### Post by Professor X on 2005-05-06
[This guide](http://www.ubuntulinux.org/wiki/HowToCygwinX) might help you.  

Other people have had similar issues with XDMCP.  [See this post](http://ubuntuforums.org/showthread.php?p=139766).

 Good luck.

---

### Post by rmmcgr on 2005-05-06
Thanks, but I have already had a look at the wiki page and the post and nothing in there got me going.

I guess it would be good to know if anyone else has followed those guides and found that it worked for them with hoary.

..Richard

---

### Post by sugna on 2005-07-14
I'm currently in the same boat.  I'm trying to get an XDMCP session going with Cygwin/X on WinXP.  I get the Ubuntu login, but then just a blank brown screen.  I've done all I can from the Wiki and posts.

Will report any progress!

---

### Post by sugna on 2005-07-14
I just tried X-Deep/32 (a different X server) and got the same result.  So I'm thinking that the problem is most likely at the Ubuntu end.

I really want this to work.  Any help will be most appreciated!!

---

### Post by rmmcgr on 2005-07-14
I installed Xfce 4 (at the console) and then was able to get that to come up.  So at least I have a GUI that I can access remotely, which was what I was really after.

But it would have been nice to have the full Gnome experience.

Thanks,
Richard

---

### Post by sugna on 2005-07-14
OK, I installed xfce4, but I'm not quite sure where to go from here.

The online doco says that xfce can happily coexist with gnome somehow if you follow the instructions at [http://www.xfce.org/index.php?page=documentation&lang=en](http://www.xfce.org/index.php?page=documentation&lang=en).  But so far the only way that I have managed to start xfce is by restarting gnome (actually it seemed more like terminating -- I typed gdm-restart) and entering the command 'startxfce' from a text-only environment.  Cygwin/X just gave me the usual results.

What further configuration steps will I need to do to prepare xfce for xdmcp?

---

### Post by sugna on 2005-07-15
The experimentation continues . . .

I've turned my attention to trying to get my Ubuntu box to connect with XDMCP to another Ubuntu box (both using Gnome).  After some stuffing around with the firewall and gdm.conf file, it works like a charm!

Still no luck with Cygwin/X and my XP box though.

At least I know now that my Ubuntu boxes *can* successfully run xdmcp.  They're just not talking properly with Cygwin/X (or with X-Deep/32, for that matter).  Perhaps it's time to revisit the Cygwin/X mailing list . . .

---

### Post by bestone on 2005-12-09
I also had the same problem, I was also thinking that my firewall could not be the problem. Then I check the firewall journal, and I noticed a lot of block UDP packets at the time i was trying to connect via XDMCP.
I de-activated the firewall, and it works.

The problem that I have now, is i don't know yet how to let the firewall not block udp on port 177. I tried already many things, but just don't work.
If someone has any info on AVG 7.1 ... ?

But at list now i know it was for sure the firewall. Hope this would help you.
:D

---

### Post by sugna on 2005-12-10
Gee, it's been so long now that I can hardly remember what I had and hadn't tried to get it working.  And I've barely used the old Ubuntu box since.  I'm certain that I tried disabling the firewall at the Ubuntu end, but I can't remember if I disabled the firewall on my XP computer (though if I was being systematic about it, I would have).  Which firewall did you deactivate in order to get things working, bestone?

---

### Post by neojinux on 2005-12-23
I change my WinXp firewall to bypass:
TCP 6000
UDP 177

Everything work fine now

Reference
[http://x.cygwin.com/docs/faq/cygwin-x-faq.html#tbl-xdmcp-ports]("http://x.cygwin.com/docs/faq/cygwin-x-faq.html#tbl-xdmcp-ports")

---

### Post by sugna on 2005-12-24
Well I'll be darned.  I disabled Kerio Personal Firewall and the Cygwin/X XDMCP session actually worked!  I always assumed that the firewall on my Windows PC was not the problem because it gave me no notifications or suspicious messages.

But so far I have been unable to define a rule for Kerio that will enable XDMCP to work while the firewall is actually running.  In fact, according to a message on the Kerio forum, the problem might actually be Kerio itself:  [http://forums.kerio.com/index.php?t=msg&goto=31793&S=84d4585d18be21d6b4eef0d0aea2400f#msg_31793](http://forums.kerio.com/index.php?t=msg&goto=31793&S=84d4585d18be21d6b4eef0d0aea2400f#msg_31793)

What firewalls are other people using at the Windows end?  Has anyone managed to get XDMCP to work with Kerio?

---

### Post by sugna on 2005-12-24
I just ditched Kerio and installed Jetico Personal Firewall.  Cygwin/X now works beautifully!

---

### Post by soongwoo on 2006-02-27
Could you explain it in detail?
I mean what you do in Ubuntu box and Windows XP.

I had been using CygwinX bwtween FC4 and Windows XP, not Ubuntu.

Thanks
soongwoo

---

### Post by sugna on 2006-02-27
Ugh, it was so long ago!  And I haven't used it much since.  But I'll do my best.

I remember going through a general XDMCP 'howto' document (just google it and you should find it fairly easily) and following all the instructions that seemed relevant to Ubuntu.  But to be honest I don't know whether or not that was actually necessary because at that point things just weren't working, and now that they are working I haven't undone any of those steps to see what happens.  So you might want to ignore this step until you've tried everything else.

Apart from that, I would have opened the necessary ports on my firewalls (177 and 6000 or something like that -- the Cygwin/X documentation has a section explaining this), and ticked the 'allow xdmcp' option(s) in the login preferences of Ubuntu.  Just don't use Kerio Personal Firewall!!

To run Cygwin/X, I used the .bat file "startxdmcp.bat", located in C:\cygwin\usr\X11R6\bin\.  Currently the line in that file that makes everything go is:
%RUN% XWin :0 -query %REMOTE_HOST% -nodecoration -lesspointer -clipboard

The ":0" might need to change to :1 or something depending on whether you are already logged in at the Ubuntu end.

Earlier in the batch file I inserted the local IP of my Linux box in the line:
SET REMOTE_HOST=

And I think that's about it.  That's all I can remember for the moment anyway.  I'll report back if I remember anything else important.  Feel free to ask some more specific questions to jog my memory.

Good luck!

---

### Post by soongwoo on 2006-02-28
Thanks for the reply. I should get the howto somewhere else.

soongwoo

---

