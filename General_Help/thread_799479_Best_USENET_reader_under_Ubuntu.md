---
title: "Best USENET reader under Ubuntu?"
date: 2008-05-19
forum: General Help
---

### Post by clanmackay on 2008-05-19
What have people found to be the best graphical USENET reader under Ubuntu?  I would like something that displays threads in a proper tree, that can automatically check for new messages and alert me to them (with a sound or arbitrary command, say), and that allows differing profiles (with different sigs, etc.) for each ng.

So far Pan is working best for me, but I cannot figure out how to make it check automatically for new messages.

In Thunderbird, I cannot figure out how to make the messages show up in proper tree form; the whole thing is flattened to one layer and sorted by time.

Thanks!

---

### Post by Shazaam on 2008-05-19
I run Grabit in wine. It's a little slow but it works fine.

---

### Post by andrew.46 on 2008-06-05
Hi,

When you nominate only 'graphical' readers you have removed consideration of some great newsreaders. I speak especially of slrn.

            Andrew

---

### Post by oldos2er on 2008-06-05
Here's a second vote for slrn; tho' it's text-based, it will properly display threads. Visit "Andrew's Corner" (see above post) for more info.

---

### Post by clanmackay on 2008-06-05
> **oldos2er said:**
> Here's a second vote for slrn; tho' it's text-based, it will properly display threads. Visit "Andrew's Corner" (see above post) for more info.

Certainly, I will check that out.  Thank you.

---

### Post by andrew.46 on 2008-06-06
Well actually there is an 'Ubuntu' version of this page that might be a better choice than the web site mentioned:

[http://ubuntuforums.org/showthread.php?t=475246](http://ubuntuforums.org/showthread.php?t=475246)

The web site version is substantially less friendly :-).

      Andrew

---

### Post by clanmackay on 2008-06-06
> **andrew.46 said:**
> Well actually there is an 'Ubuntu' version of this page that might be a better choice than the web site mentioned:

[http://ubuntuforums.org/showthread.php?t=475246](http://ubuntuforums.org/showthread.php?t=475246)

The web site version is substantially less friendly :-).

      Andrew

[heaves sigh]

OK, I've got it installed from source, running, and I've strapped on my spiked climbing shoes for the learning curve.  Maybe I'm getting too old for this.  I love power tools like this, but the key bindings are brutal to learn -- at least in one hour.

A couple of questions:

1. I edited my .slrnc file to specify a default editor and web browser, following Andrew's instructions.  Neither choices are being honored:

```

set editor_command "emacs -nw '%s'"
set mail_editor_command "emacs -nw '%s'"
set post_editor_command "emacs -nw '%s'"
set score_editor_command "emacs -nw '%s'"
set Xbrowser "firefox '%s' &"

```

2. When I go to post a message, it lists me as USERNAME@HOSTNAME.  I think this is the same problem as #1, yes?  .slrnc not being respected?

3. I'm sure there will be more.

---

### Post by cariboo on 2008-06-06
Give **pan** a try. I haven't used a newsreader since I was beta testing Xandros v1, but it seemed to have all the things you're asking about. Its available in the repositories

Jim

---

### Post by andrew.46 on 2008-06-06
Hi,

It is always a little exciting when someone starts using slrn. Ubuntu has produced a few regular users recently, I suspect more so than other distros.

> **clanmackay said:**
> 1. I edited my .slrnc file to specify a default editor and web browser, following Andrew's instructions.  Neither choices are being honored:

Possibly you have made a glorious typo in naming your configuration file:

```
~/.slrnc
```

instead of the required:

```
~/.slrnrc
```

If so that is an easy fix :-). Don't forget to drop in on news.software.readers if you have any problems. There is always a warm welcome for new slrn users, although your choice of emacs guarantees a little good-natured ribbing!

    Andrew

---

### Post by sune_cph on 2008-06-06
My vote for PAN as well!

/Sune

---

### Post by clanmackay on 2008-06-06
> **cariboo907 said:**
> Give **pan** a try. I haven't used a newsreader since I was beta testing Xandros v1, but it seemed to have all the things you're asking about. Its available in the repositories

Jim

Right.  As I wrote: "So far Pan is working best for me, but I cannot figure out how to make it check automatically for new messages."  But in general I like it a lot.  There will have to be big payoffs for switching to a new one.  :-)

---

### Post by clanmackay on 2008-06-06
> **andrew.46 said:**
> 
Possibly you have made a glorious typo in naming your configuration file:


*Man*.  Where's a frying pan when you need it?  I need a smack upside the head.

Sorry about that, seems to work now.  Have I mentioned I *really* like it?

Very exciting, now that it "heels".

Thanks.  I'll probably have a few more questions shortly.

---

### Post by cssutto on 2009-01-19
Andrew:

I can not post a message with slrn.

I keep getting the message (flashes so fast that I can't get it all) that my log on name does not match whatever.

I have screwed with my hosts file, user name, real name, slrnrc file etc. for days and can not get it to work.

It worked in Ubuntu 7.10 but when I updated to 8.04 it did not.

I can log on and read news, I just can not post.

My hosts file is:

127.0.0.1       localhost
127.0.1.1       claude69694-laptop.suttonmachine.com     claude69694-laptop
                127.0.0.1 localhost.localdomain localhost claude69694    #claude69694
               192.168.0.1 claude69694.suttonmachine.com claude69694 ##KR1
                 192.168.1.13 claudesutton.suttonmachine.com claudesutton

                74.202.151.42 suttonmachine.com ##cleese.icomdesign.com


My slrnrc file is:

%set hostname "claudesutton,suttonmachine.com"
set hostname "suttonmachine.com"
%set hostname "claude69694.suttonmachine.com"
%set hostname "suttonmachine.com"

%set username "claude69694"

%set username "claude69694"

set realname "Claude Sutton"

I include some of the entires I have tried without success for information.

The logon name to log on to my machine at startup is:

claude69694

The command line in the terminal is:

claude69694@claude69694-laptop:

How all of this fits together is a mystery to me!

Any suggestions would be appreciated.

By the way, I have read your web page many times.  I just don't get this part of it.

Everything else works.

CSSJR

If we do not wish to lose our freedom, we must learn to tolerate our
neighbor's right to freedom even though he might express that freedom
in a manner we consider to be eccentric.

---

### Post by cssutto on 2009-01-19
I withdraw my question.

It is not slrn.

It is a requirement of News.GRC.com that I cam not meeting.

CSSJR

---

