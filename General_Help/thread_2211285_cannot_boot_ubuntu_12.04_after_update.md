---
title: "cannot boot ubuntu 12.04 after update"
date: 2014-03-15
forum: General Help
---

### Post by antunny on 2014-03-15
hi

I am new to Ubuntu.  I have windows 7 64 bit home premium and was sick of it crashing apparently after every update, so I thought it was good time to try Ubuntu.  I have had it installed about 6 weeks, however have hardly been able to use it due to lack of time.  whenever I went into it it seemed fine.  main thing I did in Ubuntu was run the updates, and when I updated last sunday (9th march) and I either clicked restart or shut down, then I could not get back into Ubuntu.  I have tried many times, it boots normally about 1 in 5 times, other times I (mainly) get a page of white text on black screen, smallish font, and among the many words I can distinguish the words 'page break'.  I have tried various recovery options, including repairing broken packages, updating grub, with various success, including getting into Ubuntu with wonky graphics. I must stress that if I fiddle, I can get in normally, but it will take several attempts; also, sometimes on the blue screen where I choose between Ubuntu and windows, the countdown in seconds is there, sometimes not.

I have tried boot-repair from the cd, following instructions from the internet and also from the manual for 12.04  and yesterday I reinstalled Ubuntu 12.04 from the cd, however, first thing I did was run 60 Mb of updates and the same problem occurred - the page with all the text and it is frozen.  however, I am not entirely sure if I am applying the correct remedy (the manual refers to problems after installing windows, which of course is not my issue).  

obviously I chose Ubuntu because I was sick of windows crashing after updates but I seem to be in exactly the same position with Ubuntu.

perhaps I should also mention that for my own reasons I have been running Ubuntu with French as the main language, but at present the culprit would appear to be the update last sunday - unless that is the only time I have chosen 'restart' as an option and that is the problem.

also I should stress I am more or less completely new to Ubuntu. 

unless there is a relatively straightforward way of solving this annoying issue I think it would be easier for me to uninstall Ubuntu and go back to windows, although I liked what I briefly saw of Ubuntu and would like to keep it.  therefore, any pointers to uninstalling Ubuntu from windows 7 (can I use disk management facility?) would be appreciated.

sorry if this rambles too much........

many thanks

---

### Post by craige2 on 2014-03-15
Hi there,

sorry to hear you're having problems.

I think, you updated your kernel or something and you caused an issue with your graphic cards drivers. Would be good if you could share some details for your pc, do you have ati/amd or nvidia?

Usually what I do before I update, I check if there are any entries for kernel, headers etc. If so, I purge remove my graphic card drivers, do the update, check if there are packages left behind, reboot, install graphic's drivers and then reboot again. 

Of course would help if you got your graphic drivers on a folder on stand-by for these situations.

You can also choose to update some other time. I got a pc running Ubuntu 11.04 and still operates fine, without doing any updates at all. Update when you want not when it tells you, it's not like windows.

What you need to do, I think at least is:

a) Ctrl+Alt+F2 to go into terminal
b)purge remove you graphic cards drivers. Check online how to do that, depends if its ati or nvidia, or give the information and someone would reply here.
c)install kernel, do update,upgrade, install packages left behind, especially kernel headers etc.
d)install your graphic card's drivers.


**That's how I tackled a similar situation. However, since I am new as well, wait for more experienced people to check on this and do suggestions. **


If you insist to go back to windows, just pop in the cd, and follow the options. Do not install them alongside on disk, choose the entire disk. 


Hope it helps.

CR

---

### Post by antunny on 2014-03-15
hi craig

thanks very much for your help.  

I probably should have mentioned, I have dual-boot (??), I have windows and Ubuntu alongside each other.  so if it comes to removing Ubuntu, I wondered if I can do it from inside windows 7 disk management facility.  anyway, hopefully I will be able to continue with Ubuntu

I have tried to find out which graphics card I have.  could it be intel(r) hd (I found this on system info in windows)?  I am  not very familiar with graphics cards and to be honest would be a little uncomfortable uninstalling and installing drivers............could this stop Ubuntu booting up?  when I said I sometimes experience 'wonky graphics' it was after using one of the options in recovery mode and there was a warning that the graphics could be out of sync - the other times when I actually got in the display was fine, or when I did not get in as I said I got various screens of text  - by the way the phrase I saw was page fault I think not page break

forgive the stupidity of some of my questions: kernel - that is the system files?  like the engine of the operating system?

in my browsing of internet and this website, I came across a similar problem where the solution lay in choosing 'previous Linux versions' on the initial screen - I tried this since my initial post and I got in ok, I tried again just now before coming here and it worked, I tried restarting and it was ok -however I have not done anything like run updates in there because I am not too sure where I am!  is this the version of (what?? - system files??) before my last update?  because the numbers in 'previous Linux versions' do not match the numbers in the other entry into Ubuntu (neither contain 12.04) - they begin with '3'.  the post I saw contained the advice to use something called 'synapsis' (??) to change the default Linux version to the 'previous Linux version' - hope this makes sense!

I have conscientiously run all the updates because I am paranoid about security, and I note that some of the updates are security updates. perhaps I should have just run the security updates?

I am worried if I uninstall drivers for graphics card I may mess up my version of windows which if Ubuntu does not work is the only system I will have!

antunny

---

### Post by msfin303 on 2014-03-15
Hi Antunny
Sorry to hear you are having trouble with your system crashing. Intel HD drivers for both windows and Linux are extremely reliable. 

This may sound crazy this may not be a software related.

I don't know if this is of any help
The fact that you are having issues with it crashing with both windows and Linux, from past experience does point to a hardware issue. 
A few things you may like to try...
Go to the site of you PC manufacture, and look to see if there is a BIOS update. 
If there is .... Follow their instructions for updating.
Also go into the bios and look to see if there is anything unusual in the settings (or restore to the default settings and save)  .
I know this may seem odd thing to do, even just go into the Bios ... hit F10 (save and exit) has worked in the past for me. 

Also is the Pc getting hot?... (blow through the air vents like a harmonica to get the dust out)   

Hope this is of help :-)
Sean

---

### Post by antunny on 2014-03-16
hi sean

thanks very much for your reply

to be honest, it has occurred to me - especially when I just had windows 7 on my computer and it kept crashing (only had it less than 18 months) if it was the computer, but as it only really occurred when Microsoft inflicted updates on me I assumed it was their fault - also I am pretty sure I saw posts from other people with windows 7 64 bit home premium that had the same problem

and there do seem to be plenty of people here who have trouble after updates

I am not aware of the computer becoming particularly hot (it is a laptop)

I think I mentioned in my last post that I tried out the 'previous Linux versions' at the original screen where I choose which OS to use, and I have not had problem going in and coming out that way.........I found something last night which suggested it is possible to change the default OS at that screen to one of the previous kernel versions - I was thinking of giving it a go with that version.  it seems just the same as the version I was using before I had problems.  

I tried to find BIOS update for my computer - Toshiba satellite c660-26z - naturally, discontinued only 16 months after I bought it! - and when I go to their bios update page it will not let me drill down any further than c660 (they call it a notebook but I thought I bought a laptop!).  I will however go into bios and see if anything looks unusual to me.........however, I am not a pro so it all looks a little unusual to me.

thanks very much for your help, I really appreciate the trouble people have taken to reply and help me

antunny

---

### Post by craige2 on 2014-03-16
Hi antunny.

Seems you have more than one problem to tackle :( . It might seems tough now but if you be patient and walk through once, the next time would be like a walk in park. It's only until you find the way to set up your machine, it's not same for all. 

The different versions you see on start up, it's because you updated to different version, not distribution. The Ubuntu keeps the previous config in cases like yours, something happens and you want to roll back to a working state. However you will need to deal with the updates and kernel/graphics drivers sometime in future again.

Other than what I suggest in my first reply, I could only think a couple of options to consider doing:

a)Have you consider virtual machine? You could have for instance Ubuntu as main OS and install windows on a Virtual machine, if you need to access your windows specific programs(unless it's games, in this case virtual machine and gaming is crap, don't do it.). It's what I have at the moment. You could do the vice versa of course.

b)Check if your Ubuntu distro is playing "nice" with your graphic card. There are several alternatives, Kubuntu, Lubuntu etc. Check if your drivers and the environment is at good state at the moment. Maybe it would be a less of headache if you try another one. Especially check the combination kernel version-drivers-environment.

c) Again I will pop up the update part. Find a way to deal with kernel and re-install drivers. It is usually 2 lines commands, at least for my case. Search for "purge uninstall (your drivers)". You will have to do it at some point.

d)Since both your OS are in need of "attention", would you consider a format or a clean install? You could also wait till next month to get the new version of Ubuntu as well for that. 

*You do not have to lose anything. You always have your previous configuration to roll back. Experiment with your machine until you get it up. Next time would be most likely an easy do-over. Personally I have stored the drivers and the commands I need on a file and I just copy paste them. After a while it's that easy.*

I think you should consider what you want to do the machine to be like. Then, since it's more than one problem, choose one to begin.

Also, I saw you mentioned security on previous posts. If by that you mean, virus etc, do not worry about. Your machine is safe without the updates. 

Best of luck mate. 

CR

---

### Post by antunny on 2014-03-18
hi
what are the chances that they will fix this issue on a later update?  i can't be the only person this has affected.

if i upgrade, am i likely to have the same problem?  i am very much tempted to upgrade if there is a chance i will not have this issue.

if by format you need take everything off my hard disk, no i'm afraid that does not appeal

i'm afraid i still do not understand: my 'distro' is what i downloaded and installed?  and the 'previous linux version' is what - an earlier version of the 'kernel'?  if i use that i cannot obtain updates?

have searched and have not really found satisfactory answers to how to 'purge drivers', so i am afraid it still sounds beyond my capabilty at present

 also i don't understand what is going on - i found posts about a linux driver for intel (cards??) which was unsatisfactory and had to be uninstalled (my graphics card appears to be intel(r) hd)

i went into system settings and my graphics card is not recognised by ubuntu

if i am uninstalling drivers (if i do chance it) i am doing it from where - command line?  in ubuntu?

what you do is you uninstall graphics card drivers once you are in ubuntu, you update kernel (i imagine these updated are signposted as such??), then re-install drivers?  do i understand?  and - again, forgive my naivete - what is the effect when you uninstall the drivers?  or do you do the update from a command line as well?

sorry, I really am new


antunny

---

