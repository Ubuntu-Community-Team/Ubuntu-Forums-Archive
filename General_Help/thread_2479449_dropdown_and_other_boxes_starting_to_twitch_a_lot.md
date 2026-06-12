---
title: "dropdown and other boxes starting to twitch a lot"
date: 2022-09-24
forum: General Help
---

### Post by jgw on 2022-09-24
dropdown and other boxes expecting an import (y/n, name, address, etc) starting to twitch a lot.  Sometimes more, sometimes less, have no idea why.  Sometimes I might, for instance, left click on a forefox tab and press 'delete'. Iit might take my 5 or 6 times before I can put my pointer on 'delete'.  Same for all that stuff.  If I am trying to login someplace and they want a name it also gets  a bit adventuresome.  

Thoughts?

---

### Post by MAFoElffen on 2022-09-24
Which NVidia driver and which Graphics Engine are you running (X11/XServer or Wayland)? Running the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") will answer a lot of those questions and more about which Theme you are running and what some more of your graphics settings are...

---

### Post by jgw on 2022-09-24
Thanks for the reply!

I did the system-info thing but couldn't find the file.  I did it 3 times and no file.  I read all the stuff but couldn't find the name of the file or where it might be.  I still have the program if you could tell me where to find the file I will put it into ubuntu pastbin if I can find it.

---

### Post by MAFoElffen on 2022-09-24
The report file is called 'system-info.txt' and it's located in your Home directory... 

If you select yes by typing <y><Enter> at the prompt, it uploads the report to a pastebin... 

If you already did that and you missed where it had the link to where it was uploaded, if you look at 'system-info-link.log' file (in your home diretory), that also has the link for that... So you can post the link for that in a post.

---

### Post by jgw on 2022-09-25
So, you got the report?  I'm at a different machine but will take a look later.  Thanks for letting me know!

I did that thing once before but never had the problems.  I think I am in a rut of problems on a lot of stuff.  Getting old, I fear.

---

### Post by MAFoElffen on 2022-09-25
True. I am the author and wrote it for members of the Forum to use to help diagnose people's computer problems, but... The location of the pasrebins do not 'come' to me... I have no connection to pastebins, but do use them. LOL

You needed to post the URL of where the Report uploaded to a Pastebin... (It does not go to me.) So I need to know the location of it.

Please post that URL. Please.

---

### Post by jgw on 2022-09-26
First, I found a file called system-info which is 57.5kb long.  I would send it to ubuntu pastbin but forget how to do that.  I also have an account at pastebin.com which I can send it to.  When I was running the program it told me that I was missing a program called pastebiniit so I installed it.  I can also run the program again and see what happens.  I know the program works because I used it on another thing and it worked fine.  I can also send it to  [https://paste.ubuntu.com](https://paste.ubuntu.com)
OH, I looked up who told me about the program and ubuntu pastbin, it was  MAFoElffen 

I don't know where the file went.  Don't know where to go to find that out.  I can, however run it again if you wish.  I have only one system-info file on that drive and that is, I think, the report. 

Let me know what you want me to do and I will give it a try.  

Thanks for your help!

Thoughts?

---

### Post by jgw on 2022-09-29
Well, haven't heard from you so I thought I would run it again.  This time I learned the report is at:
 [https://paste.ubuntu.com/p/KXDSm3MCck/](https://paste.ubuntu.com/p/KXDSm3MCck/)

---

### Post by MAFoElffen on 2022-09-30
Thank you. The next to last post had a link, but the pastebin was blank. The last post had a pastebin with the report... 

Here we go. You have:
RS780L [Radeon 3000]GPU, which is using the Radeon driver. 
The resolution is set at 1920x1080-32. 
The Desktop is Ubuntu:gnome. 
The DE Graphical Login Manager is GDM. 
The Theme is set to Yaru.

At the lower right hand corner of the GDM graphical login page, there is a Gear Icon, select that and from the drop-down menu, use 'Ubuntu XServer'. See if that displays better for you.

---

### Post by jgw on 2022-09-30
Thanks for the reply!

Its all very strange.  I am displaying this machine on a 65" tv.  I can't remember the program but one told me that my display was 1920x1080  and then, in another part said that the real setting was (I forget but it had bigger numbers).  When I first set this up, a long time ago and a different ubuntu, it was setup with a resolution of 4096x2160  I run the machine display through a receiver that is kinda elderly but still supported by denon.  I think that changes my resolution (but not sure).  Its pretty strange.  My resolution, however, is actually pretty good!

Oh, gdm.  Seems its no longer available. I tried to install int and got:
Package gdm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gdm' has no installation candidate


The jumping boxes change from minute to minute.  Sometimes its hard to hit the right thing and other times they are solid as a rock.  I'm getting used to it (have to pay attention that whatever I am doing, took).  I have found, through the years, that computer stuff just happens and, sometimes, you get to live with it or spend your life trying to fix something that resists.

---

### Post by MAFoElffen on 2022-09-30
The package name for gdm is 'gdm3'... But your report says that is already your current Graphical Login Manager, so should already be installed.

When you first boot, does it ask you to login? Look at the attachment. At boot, when it boots to your User Name and you select it, GDM goes to the next screen to enter your password. On that screen, in the lower right hand corner, select the Gear Icon, then select "Ubuntu on Xorg". Then enter your password and go on...

---

### Post by jgw on 2022-09-30
I have my boot set to automatic login so that won't work.  I think I can change that in system settings and then make a run at that.  Is there any way to do it after boot? 

Thought I should ask <g>

---

### Post by MAFoElffen on 2022-10-01
Go to the Settings-> Details-> Users and then unlock it with your password and toggle the Automatic Login button off.

---

### Post by jgw on 2022-10-02
I've now re-booted several times trying out the options.  One thing I am not sure about is whether I have fixed the jumping boxes thing.  I am currently on the ubuntu on and think I will do that one.  The boxes are not jumping and that makes me a happy camper!  I think you have fixed my problem for which I am grateful.  

I wonder, have you ever tried a program called "hardinfo"  which is listed in Applications as "system profiler".  It produced a pile of stuff but is presented in a different way.

---

### Post by jgw on 2022-10-02
I've now re-booted several times trying out the options.  One thing I am not sure about is whether I have fixed the jumping boxes thing.  I am currently on the ubuntu on and think I will do that one.  The boxes are not jumping and that makes me a happy camper!  I think you have fixed my problem for which I am grateful.  

I wonder, have you ever tried a program called "hardinfo"  which is listed in Applications as "system profiler".  It produced a pile of stuff but is presented in a different way.      

Thanks again!

---

### Post by MAFoElffen on 2022-10-04
I have not used those... I am the project leader and Author for the Ama-Gi Project. The UbuntForums 'system-info' script I wrote and gave to the Ubuntu Forum, with the intent that it helped it's users make informed recommedations to people who need help. 

I originally wrote it using 'inxi', but that is not a utility that is a default installed utility ...meaning the user would have to try to install something that might already have problems, and might already be compromised. I rewrote it using utilities and files that should already be installed to all flavors of Ubuntu. The scope set by the focus group that worked with me also wanted it to be able to be run from an Ubuntu LiveCD USB.

Later, this script was reviewed by DistroWatch, titled "Ubuntu Gets New Tool:, saying it worked great, with few gaps in information, for other Linux Distributions. After that review, I rewrote it to work with Ubuntu 22.04, and to work with other Linux Distributions. I then informed the editor when the new release was released, so he could test/play with it more. (LOL)

So if this is resolved, please use the "Thread Tools" link at the upper left of this page to mark this thread as "Solved" so that others can see your solution for their similar issues.

---

### Post by jgw on 2022-10-04
No more jumping boxes so far!  Thanks again!

---

