---
title: "[SOLVED] ...upper memory..."
date: 2008-04-25
forum: General Help
---

### Post by CaptainOblivious on 2008-04-25
The thread I found via Google didn't really have a resolution.

Installed with Wubi to Hardy Heron.  Upon booting to Ubuntu, the screen immediately states

"...upper memory..."

Yeah.  That's real helpful.
Anyway, I can't access the verbose boot mode.  pressing insert a lot does nothing.  Would anybody like to speculate as to how I might fix this?

Thank you in advance.

---

### Post by tinybit on 2008-04-25
probably you are using normal gnu grub 0.97, not the grub4dos. The Insert feature is only available with grub4dos and not with gnu grub 0.97.

and grub4dos does not display "upper memory". Instead it shows "Memory upper/lower".

---

### Post by CaptainOblivious on 2008-04-25
If that's the case, why did Wubi download the incorrect files to use?  If I'm a Windows user, and it claims I can basically install Ubuntu in two clicks and a long download, I expect that to be the case.

Now I appreciate your input, but this still doesn't help me solve the problem.

---

### Post by ago on 2008-04-26
Are you using grub at all?
Also what happens when you press insert rapidly as soon as grub/grub4dos starts? Do you see a countdown?

---

### Post by bean123 on 2008-04-26
What's the exact message displayed on screen ?

---

### Post by silentlun on 2008-04-26
I'm facing the same problem with the "...upper memory..." after installation. I've attempted pressing the insert button but it does nothing. Would I need to install grub4dos separately? Did the wubi that was included in the latest release of Hardy Heron download the  wrong files? Thanks a bunch.

---

### Post by ago on 2008-04-26
Wubi should install the correct grub4dos, and you should see some wubildr* files in the root folder as well as c:\ubuntu\winboot

Anything peculiar about your setup? Particularly when it comes to bootloaders?

---

### Post by silentlun on 2008-04-26
Well my hard drive has been partition into 3 parts C, F, and G. C is obviously for windows, F is for my program files, and G is for any other types of files such as pictures, videos, documents.
I have wubi installed in the C drive and yes it does have the files you mentioned. When I boot it up, it gives me the windows boot menu, then i choose ubuntu. Afterward a "...upper memory..." error on the type left screen.

---

### Post by silentlun on 2008-04-26
This is what my boot.ini looks if it helps.


[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

---

### Post by ago on 2008-04-26
Is "...upper memory..." EXACTLY as it appears on screen char by char (with dots and spaces)?
Is there a space after the 3rd dot? "... upper memory..."

---

### Post by ago on 2008-04-26
I believe that this is a Gate A20 issue in fact:

http://www.google.com/search?q=grub4dos+"Turning+on+gate+A20"

---

### Post by ago on 2008-04-26
Unfortunately this looks like a gate A20 issue. And that means that your machine/bios is not supported by grub4dos. The only solution at this stage is to use proper grub 0.97,  which means you have to do a full installation from CD and cannot use wubi.

---

### Post by silentlun on 2008-04-26
Ahh. ok. I kind of figured being that it is an older dell machine I was testing wubi on. Thanks for your help. I guess I'll need to repartition my hard drives. Oh well. Good thing Ubuntu made that easy. I really wanted to test wubi out too.

---

### Post by silentlun on 2008-04-26
I hope a new version of grub4dos will work later on.

---

### Post by mikeman141 on 2008-04-26
I too have been having this same problem with a dell.  I want to use grub 0.97, but I can't seem to figure out where to get it from? The ubuntu website only seems to allow downloads of the cd image I have...can somebody link me or explain how I can get/use grub 0.97?

Thanks

---

### Post by ago on 2008-04-26
As mentioned, if you have an upper memory error or a gate A20 error, it means you cannot use wubi on your machine. 

You can still try Ubuntu via the live CD (read only) and install it using the CD. As part of the Ubuntu installation you will also get grub 0.97.  

To tell the full story, it is possible to install grub 0.97 separately and even make it work with Wubi. But it would be quite a complex operation. Best route is to go for a full installation using the CD.

---

### Post by tinybit on 2008-04-26
how to make an original old 0.97 version of grldr?

here is it.

1. compile gnu grub 0.97 and you will get the pre_stage2 file.

2. compile grub4dos latest and get the grldrstart file

3. cat grldrstart pre_stage2 > grldr

in step 3, the grldrstart is from the grub4dos and the pre_stage2 is from old gnu grub 0.97. Then the ending grldr can be used normally, except you have to use original grub commands only and the extensions by grub4dos cannot function.

if you succeeded in this way, please drop a line.

Note: you will or won't encounter problems when you try to change the menu.lst pre-set in this GRLDR. Don't try to change the name of GRLDR, nor anything else of GRLDR, because you only try to experiment with this GRLDR. if you can see a grub prompt and enter commands, then we consider this as a success.

---

### Post by bean123 on 2008-04-27
Actually, there is no need to recompile, you can use loadbin utility to create boot files for GNU GRUB. Please extract the files in the attachment and put them in C:\, then, add the following lines at the end of C:\boot.ini:

C:\grub.mbr="GRUB"
C:\grub2.mbr="GRUB2"

After reboot, you will see the two extra menu item in the nt boot loader. If all goes well, you will go into console mode with the grub> prompt.

Note: if you use vista, there is no boot.ini, you need to set the boot menu using bcdedit.

---

### Post by ajayappa on 2008-04-27
I've the ...upper memory... problem after installing wubu and rebooting, selecting ubuntu

i followed suggesting in earlier posting and i can see grub and grub2 in boot options.

now what ..? i want to load ubuntu.

---

### Post by ago on 2008-04-27
copy the c:\ubuntu\winboot\menu.lst to c:\ and try to reboot
That uses find --set-root and from the above it looks like it may fail ("you have to use original grub commands only and the extensions by grub4dos cannot function"). 

If it fails copy c:\ubuntu\install\boot\grub\menu.lst to c:\

But you have to replace all the lines that start with "find --set-root" with 

root (hdX,Y)

X indicates the disk number -1, and Y the partition number -1. You have to put appropriate numbers to point to the partition where you installed Wubi.

---

### Post by CaptainOblivious on 2008-04-28
First, I want to thank everyone who has chipped in with suggestions.  You are awesome.

I have followed the GRUB and GRUB 2 step and I can successfully boot into each now.

Now, lets say I have never used Linux before.  Without taking any shortcuts in describing it to me, what is the process in getting Ubuntu to boot from this stage?  Grub and Grub Recovery load and await commands.  My Wubi-made installation has completed successfully to the default locations.  Are there files I yet need to change to make this process work?

I'm only steps away.  Thank you for your time.

---

### Post by tinybit on 2008-04-28
@ago

I imported A20 code from grub2 and made a build of grub4dos:

[http://grub4dos.jot.com/WikiHome/grub4dos-0.4.3-2008-04-28-a20testonly.zip](http://grub4dos.jot.com/WikiHome/grub4dos-0.4.3-2008-04-28-a20testonly.zip)

You may check, as an alternative(workaround), whether or not it works for the problematic machines.

------------------

@CaptainOblivious

You may wait for ago and see if he would soon build a special wubi version for you.

---

### Post by CaptainOblivious on 2008-04-28
@tinybit

Sounds all right to me.  Is there anything I can do to provide you with any further useful information?

---

### Post by bean123 on 2008-04-28
> **CaptainOblivious said:**
> @tinybit

Sounds all right to me.  Is there anything I can do to provide you with any further useful information?

I think you can download the above attachment, extract grldr and place it in C:\, then add the following line to boot.ini:

C:\grldr="Start GRLDR"

if you are able to see the grub> prompt, then grldr is working.

---

### Post by ago on 2008-04-28
> **tinybit said:**
> I imported A20 code from grub2 and made a build of grub4dos

That's great news. I cannot do a wubildr customization to simplify people life at the moment (not on my linux machine). To do that the embedded menu has to be the one you posted the other day (with fallbacks), and the name has to be wubildr and wubildr.mbr (pointing to wubildr). This way people can just replace the files in C:\ and C:\ubuntu\winboot. I can do that tonight/tomorrow.

Is this suitable for SVN? If so I can add to the new builds directly.

---

### Post by tinybit on 2008-04-28
Sorry. I am not sure if it is ready to commit to svn. It is for test only at  this moment. But if bean123 would decide to commit, I agree.

---

### Post by ago on 2008-04-28
Here is my remix. Unpack the attached file into C:\ and C:\ubuntu\winboot


Tinybit I used dd to extract 8192 bytes off wubildr to create wubildr.mbr.

---

### Post by uknowgary on 2008-04-28
My installation got stucked with the message "turning on gate a20" :(

---

### Post by tinybit on 2008-04-29
> **uknowgary said:**
> My installation got stucked with the message "turning on gate a20" :(

I am sorry I made a mistake. Try the build 2008-04-29 please: [http://grub4dos.jot.com/](http://grub4dos.jot.com/)

---

### Post by ago on 2008-04-29
New remix with 20080429 tinybit  grub4dos build. Unzip into C: and C:\ubuntu\winboot

---

### Post by uknowgary on 2008-04-29
Thank you guys. It worked like a charm :) Now I'm happy.

---

### Post by Deadpixel1221 on 2008-04-29
I have unzipped all the files into both folders and I'm STILL getting "upper memory" error, please help! :(

---

### Post by ago on 2008-04-29
if the error reads "upper memory" you did not replace the right files... If you did it correctly and it fails the error should be "Turning on gate A20". Delete first all wubildr* from all drives and any /ubuntu/winboot folder.

---

### Post by Deadpixel1221 on 2008-04-29
I've solved it by installing Wubi on a different drive, I initially  
had it on my D:\ drive then uninstalled it, and reinstalled it on me C:\ drive. I don't know if that was the reason for the error but it's working fine now. I might have overwritten the wrong files as a result. :)

---

### Post by ago on 2008-04-29
after installing did you also replace the wubildr files?

---

### Post by ajayappa on 2008-05-03
Thanks Guys, I no longer get the ...upper memory... error and am posting this reply from within my newly installed ubuntu os.

I had a 3 yr old dell laptop running windows xp and I was trying to use wubi. After installing wubi, I unzipped the wubildr.zip posted earlier to c:\ and c:\ubuntu\winboot. Now I can boot both windows and ubuntu successfuly.

---

### Post by choicefresh on 2008-05-12
Epic failure.

I spent three hours trying to get Ubuntu to work with Wubi, just to find out that it doesn't work on an Intel Core2 Duo with Windows XP Pro.

The fix didn't work either, I just got another error message.

LiveCD works for me.

---

### Post by bean123 on 2008-05-13
> **choicefresh said:**
> Epic failure.

I spent three hours trying to get Ubuntu to work with Wubi, just to find out that it doesn't work on an Intel Core2 Duo with Windows XP Pro.

The fix didn't work either, I just got another error message.

LiveCD works for me.

Can you give more details, what's the error message ?

btw, I think cpu modal is not relevant, it's usually bios or file system that cause problem with grub4dos.

---

### Post by usafle on 2008-05-19
Ok, I followed all of your guys instructions and I can boot into Ubuntu "sort of".  I downloaded that zip file and overwrote the files on my C:\ drive and the C:\ubuntu\winboot

When I select to boot into Ubuntu I no longer get the 'upper memory' error I get a command prompt that says:

"grub>" 

or something to that effect.

What in the heck do I do after that to get ubuntu to actually start?  You guys gave all the answers to getting rid of the 'upper memory' problem and then just stopped after that.  LoL

Any help?

---

### Post by tinybit on 2008-05-19
1. Boot into your Windows.
2. Find the menu.lst file.
3. Copy menu.lst to the root directory.
4. Reboot and select ubuntu option and see if your can start ubuntu normally, if not, continue with the following step.
5. At the grub prompt, type these:
```

find --set-root /menu.lst
configfile /menu.lst

```

---

### Post by ago on 2008-05-20
You can copy the menu.lst from C:\ubuntu\winboot

---

### Post by usafle on 2008-05-20
Ok, I will give that a try.  
Thanks for the help.

---

### Post by usafle on 2008-05-20
Ok, first post from a successful install of Ubuntu.

No damn clue what to do next, but I am up and running.  :lolflag:

Thanks all!

---

### Post by cavitacion on 2008-05-28
> **ago said:**
> New remix with 20080429 tinybit  grub4dos build. Unzip into C: and C:\ubuntu\winboot

and then what?...

---

### Post by tinybit on 2008-05-28
And then reboot, and select ubuntu to start the installation again.

---

### Post by lwclam on 2008-05-28
I've tried to save the files in C: and C:\ubuntu\winboot
after installation, reboot again
it fail to load system, said file system error (something like that)

---

### Post by ago on 2008-05-29
please post the exact error message and/or a screenshot
also try to press insert rapidly after selecting ubuntu

---

### Post by lwclam on 2008-05-29
After I reinstall Ubuntu under Windows again and copied the files, it works find.

Thank you :)

---

### Post by surrender10 on 2008-06-26
Thanks guys, this method does fix "upper memory" problem.
:)

---

### Post by ago on 2008-06-26
Wubi 8.04.1 now fixes that, please try to install with 8.04.1 (requires new ISO) and let me know if it works ok. See the sticky thread.

---

### Post by Westergaard on 2008-06-30
Yeah.  Wubi 8.04.1 does the trick.  I was having the same problem and that fixed it right up.

---

