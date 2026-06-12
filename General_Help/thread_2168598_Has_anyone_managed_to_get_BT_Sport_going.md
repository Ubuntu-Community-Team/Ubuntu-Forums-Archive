---
title: "Has anyone managed to get BT Sport going?"
date: 2013-08-18
forum: General Help
---

### Post by mfundisi2 on 2013-08-18
[http://sport.bt.com/](http://sport.bt.com/)

Am using Ubuntu 13.04, Firefox 23 with Moonlight 3.99.03. Before installing moonlight it asked to install silverlight which obviously I cannot do. Now it simply does not play - no errors.....

---

### Post by kostkon on 2013-08-18
You could try with [Pipelight]("http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html").

---

### Post by mfundisi2 on 2013-08-18
Tried it - in both Chromium and Firefox. Showed the Silverlight test OK but didn't show any video....... 

Thanks for the suggestion - did you get it to work?

---

### Post by slackner2 on 2013-08-18
Hi,

did you install a user agent switcher? Otherwise most streaming websites will detect that you are using a wrong operating system and refuse to work.
Please take a look at this FAQ: [https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351)

Unfortunately I cannot test [http://sport.bt.com/](http://sport.bt.com/) myself as this page isn't available for my location.

Sebastian

---

### Post by mashedbear on 2013-08-22
Hey @mfundisi2 have you got bt sport working with pipelight + user agent switching?

---

### Post by texaswriter on 2013-08-22
I guess I figured this would happen sometime. Netflix is the only website I know that actually uses Silverlight (that I use anyways). I had canceled my Netflix subscription long ago due to it not working and re-enabled after the wine fix by ehoover/compholio WINE.

---

### Post by mfundisi2 on 2013-08-24
> **mashedbear said:**
> Hey @mfundisi2 have you got bt sport working with pipelight + user agent switching?

Nope - I installed the user agent switch as well as pipelight but BT Sport still shows a black rectangle and no video...

I can watch it on my Nexus 7 fortunately.

---

### Post by slackner2 on 2013-08-26
Hi,

someone on our IRC channel (don't know if he's also active in ubuntuforums) got BT Sport working by doing a downgrade to Silverlight version 5.0. (The same trick is also necessary for SkyGo.)

How to do this is described in our FAQ: [https://answers.launchpad.net/pipelight/+faq/2358](https://answers.launchpad.net/pipelight/+faq/2358)

This page moreover requires setting windowlessmode to true as described here: [https://answers.launchpad.net/pipelight/+faq/2361](https://answers.launchpad.net/pipelight/+faq/2361)
(this will not be necessary anymore when we've released our next update!)

Sebastian

---

### Post by JonPaul on 2013-08-28
Hello Sebastian

Downgrading to Silverlight 5.0 worked (I somehow managed to get two IDs with this new login system!) 

Thanks very much for your help.

JonPaul aka Mfundisi2:D

---

### Post by wolfie52 on 2013-09-11
Thank you folks...........I am digesting your comments and taking it all in. I really appreciate the time you have taken to help, and in doing so it helps me with my inexorably slow learn.
 
But I enjoy.

Geoff

---

### Post by macey on 2013-09-21
> **JonPaul said:**
> Hello Sebastian

Downgrading to Silverlight 5.0 worked (I somehow managed to get two IDs with this new login system!) 

Thanks very much for your help.

JonPaul aka Mfundisi2:D
Thanks for this, are you just using silverlight 5 or a user agent switcher also?

---

### Post by macey on 2013-09-22
polite, reluctant 'bump'

---

### Post by peter-pawood on 2013-10-16
> **macey said:**
> polite, reluctant 'bump'

I have been running it under Chromium with "User-Agent switcher for Chrome" to report Firefox version 15.0a1

(unnamed user on IRC channel ref post of Aug 26th by slackner)

---

### Post by BorisPlankton on 2013-11-04
Hi followed how to to set up for BBC sport and roll back to 5.0 but

I am stuck on

cp /usr/share/pipelight/pipelight ~/.config/pipelight


I get message saying 'cannot stat ‘pipelight’: No such file or directory'. There is certainly a file pipelight in the directory specified so must be problem with '~/.config/pipelight' command? 


I guess I must be making numpty mistake. Grateful for any advice.

On Ubuntu 13.10

---

### Post by philinux on 2013-11-04
I did notice there's a new version out now.

[http://www.webupd8.org/2013/10/pipelight-020-released-with-multi.html](http://www.webupd8.org/2013/10/pipelight-020-released-with-multi.html)

Maybe the set up instructions have changed now too. There's a link to installing in the article.

---

### Post by vishal.m.bhalla on 2014-01-02
Hi guys - just signed up to say thanks to the guys on this post. Really helped me out a lot! Here's what I did:
[COLOR=#000000]
[/COLOR]```
*[COLOR=#0000cd]# sudo add-apt-repository [/COLOR]*[COLOR=#0000cd]*ppa:pipelight/stable*[/COLOR][I][COLOR=#0000cd]
# sudo apt-get update
# sudo apt-get install pipelight
# sudo pipelight-plugin --list-enabled   [/COLOR][/I](confirm version is 5.1)[I][COLOR=#0000cd]
# sudo pipelight-plugin --disable silverlight5.1
# sudo pipelight-plugin --enable silverlight5.0[/COLOR][/I]
```[COLOR=#333333]

Start firefox, and enjoy BT Sport![/COLOR]

---

### Post by ZaphodFJ on 2014-01-13
Thanks from me too.  Easy and simple, and it works.  

Though why BT use Silverlight when the rest of the world is moving away from it, I really don't know!  Do M$ still own a big chunk of BT, I wonder?!

---

