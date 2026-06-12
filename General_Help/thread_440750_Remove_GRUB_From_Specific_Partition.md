---
title: "Remove GRUB From Specific Partition"
date: 2007-05-11
forum: General Help
---

### Post by ZodiacfreaK on 2007-05-11
gah I am such an idiot, I will try to explain this as best as I can. I have a tri-boot setup, Windows Vista, Mac OS X86, and Ubuntu 7.04 Feisty Fawn. I had grub installed and working perfectly, but then I wanted this graphical boot. Bad idea, I should have just been satisfied with what I had  but that neever works. So I went through the install steps on either page 30 in this thread, well I got to this part
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

ANd I accidently did the setup on my hd(0,2) partition instead of (0,3)
My 0,2 partition is My Mac OS X86 install. I rebooted. Well nothing changed so I went back through the steps again and this time put in the correct numbers. Everything worked but when I tried to boot into my Mac OS X partition it stalls about two seconds and then goes back to the GRUB boot screen. What I found out is that I now have GRUB installed on two partitions, I put it on my mac os partition and the other one I think is vista or linux, I dont remember . So all I need to do is figure out a way to uninstall GRUB from my mac partition. Can anyone help me with that? If you need any more info just ask!

Basically long story short, if you can tell me how to remove GRUB from a specified partition that would be the way to fix it.

---

### Post by Neobuntu on 2007-05-11
You could "remove" the (partitions) starting OS boot sector that you wrote over (with GRUBs stage 1 that usually goes into the MBR) (BTW "root hd0,x" would point to where stage 2 resides) but that wouldn't recreate your OS-X boot sector.

Don't panic. You can still read your other information off your Mac partition IF you don't have everything already backed up.

You may want to then bite the bullet and just reinstall OS-X (which you may want to do after backing everything up that you can't live without, on all partitions and also reinstalling other OS after that again too. This MAY be the fastest method.) Else you'll need to ask a mac guru the best way to install an OS-X boot sector where it's missing, if advisable.

Sorry for the bad news. I have posted warnings about using anything but GRUB's "setup (hd0)" for almost every practical situation. I suggest you also find any bad posts that may have given damaging info, quote it and ask them to edit out the mistakes.

There is a (easy) method to "backup" the OS boot sectors, per partition but that will not help you now (sorry). FYI everyone.

I believe the GRUB setup command should have a warning (when writing over anything other than the MBR) but they DO NOT make it easy to suggest/report this. I would explain it to them if I were you.

Please remember, when things go wrong, it's not necessarily a bad reflection on open software. I pray you forgive the error and still enjoy the many more positives that open software provides. After all, there really are equal ways to trash Windows or OS-X. 

You can play a BIG part by being heard in this matter.

---

### Post by m.musashi on 2007-05-11
I'm not sure you actually have grub on two partitons. When you said the
```
grub> root (hd0,2)
```
part you were only telling grub to look in that partiton for the boot files. Since there aren't any there it won't boot. If you then went back and did it again with
```
grub> root (hd0,3)
```
you simply told grub to look in the right place. Nothing is actually on the (hd0,2) partition. When you did
```
setup (hd0)
```
you wrote the setup files to the MBR not to (hd0,2) or (hd0,3).

Of course, if you did
```
setup (hd0,2)
```
Then I think it does write something to the partiton in question.

Anyway, based on what you've said, I don't think the OSX part not booting is related to grub. However, I don't have any experience with Apple hardware so I can't say for sure. That is just how it works on PCs and I suspect it's similar.

---

### Post by ZodiacfreaK on 2007-05-12
hey guys thanks so much for the responses! I really appreciate it. In answer to the first question, I am almost positive GRUB is one two partitions because the first time I went through this I did do the setup (hd0,2). Another thing I know for sure is that this is a GRUB problem and not anything to do with the way I have my Mac OS install setup, I am a little bit of a OS Quad-booting geek here :). I have trashed MBR's like no other and yet still recovered. I have never been beaten so theres no way I am backing down now :). I love ubuntu more and more by the minute, I allready have my digital audio, nvidia card, and beryl running awesome. I find Vista soo slow now. I am using ubuntu more and more every second. I just need mac os x back because it has a lot of music creation stuff I need. Although I am looking forward to installing Ubuntu Studio reps in Fesity. lol I am so lost after only having been using ubuntu for about two day :). But judging by some of the stuff I have read I allready have most of the core hardware problems out of the way, setting up my 1440x900 resolution was insane hard.

Anyways back to the problem at hand, (I love communities)
Um also this is not on mac hardware, this is a normal PC running mac os x86 ([http://www.insanelymac.com)](http://www.insanelymac.com)). But anyways, I wish there was something out there that could repair mac boot up stuff.
Oh and just for information purposes, the way I know Grub is setup on my mac partition is because of this. I went back into Vista and added Mac OS back into the Vista loader, then booted from GRUB and went to the vista loader, then selected mac OS X, and then it went to a diferent grub! So I know there are two different ones.I just wish there was some sort of command like sudo apt-remove grub hd(0,2)!!!!!!! It seems so simple, oh well. My main option right now is to backup all of my Mac OS files and then reformat the partition. Any other suggestions? :) thanks again,
ZodiacfreaK

---

### Post by ZodiacfreaK on 2007-05-12
oh and one more thing, if I have my OS X disk mounted as hfs+ in ubuntu, shouldn't I be able to see the GRUB files and remove them???

---

### Post by ZodiacfreaK on 2007-05-12
ALlright new update, I just did a search on my "Mac OS X" drive in ubuntu for GRUB andit found

```
/media/Mac OS X/usr/share/vim/vim62/syntax/grub.vim
```
Here are the contents of that file

```
" Vim syntax file
" Language:	    GRUB Configuration File
" Maintainer:	    Nikolai 'pcp' Weibull <da.box@home.se>
" URL:		    http://www.pcppopper.org/
" Latest Revision:  2002-10-24

if version < 600
    syntax clear
elseif exists("b:current_syntax")
    finish
endif

" comments
syn region  grubComment	    display oneline start="^#" end="$" contains=grubTodo

" todo
syn keyword grubTodo	    contained TODO FIXME XXX

" devices
syn match   grubDevice	    display "(\([fh]d\d\|\d\+\|0x\x\+\)\(,\d\+\)\=\(,\l\)\=)"

" block lists
syn match   grubBlock	    display "\(\d\+\)\=+\d\+\(,\(\d\+\)\=+\d\+\)*"

" numbers
syn match   grubNumbers	    display "+\=\<\d\+\|0x\x\+\>"

syn match  grubBegin	    display "^" nextgroup=grubCommand,grubComment skipwhite

" menu commands
syn keyword grubCommand	    contained default fallback hiddenmenu timeout title

" general commands
syn keyword grubCommand	    contained bootp color device dhcp hide ifconfig pager
syn keyword grubCommand	    contained partnew parttype password rarp serial setkey
syn keyword grubCommand	    contained terminal tftpserver unhide blocklist boot cat
syn keyword grubCommand	    contained chainloader cmp configfile debug displayapm
syn keyword grubCommand	    contained displaymem embed find fstest geometry halt help
syn keyword grubCommand	    contained impsprobe initrd install ioprobe kernel lock
syn keyword grubCommand	    contained makeactive map md5crypt module modulenounzip pause
syn keyword grubCommand	    contained quit reboot read root rootnoverify savedefault
syn keyword grubCommand	    contained setup testload testvbe uppermem vbeprobe

" colors
syn match   grubColor	    "\(blink-\)\=\(black\|blue\|green\|cyan\|red\|magenta\|brown\|yellow\|white\)"
syn match   grubColor	    "\<\(blink-\)\=light-\(gray\|blue\|green\|cyan\|red\|magenta\)"
syn match   grubColor	    "\<\(blink-\)\=dark-gray"

" specials
syn keyword grubSpecial	    saved


if exists("grub_minlines")
    let b:grub_minlines = grub_minlines
else
    let b:grub_minlines = 50
endif
exec "syn sync minlines=" . b:grub_minlines

" Define the default highlighting.
" For version 5.7 and earlier: only when not done already
" For version 5.8 and later: only when an item doesn't have highlighting yet
if version >= 508 || !exists("did_grub_syn_inits")
    if version < 508
	let did_grub_syn_inits = 1
	command -nargs=+ HiLink hi link <args>
    else
	command -nargs=+ HiLink hi def link <args>
    endif

    HiLink grubComment	Comment
    HiLink grubTodo	Todo
    HiLink grubNumbers	Number
    HiLink grubDevice	Identifier
    HiLink grubBlock	Identifier
    HiLink grubCommand	Keyword
    HiLink grubColor	Identifier
    HiLink grubSpecial	Special
    delcommand HiLink
endif

let b:current_syntax = "grub"

" vim: set sts=4 sw=4:
```
I'll keep yall updated if I can find anything else, I think I will digg up what the com.apple.boot.plist says.

---

### Post by ZodiacfreaK on 2007-05-12
Allright I finally found it all

THe GRUB stuff was under 
Mac OS X>private>tftpboot>private>tftpboot>boot>grub>

Now, should I just remove all of these files or would that just make the situation worse :(

---

### Post by m.musashi on 2007-05-12
Well. You've got me beat. It sounds like you need to repair the OSX partiton. If grub is causing OSX to not boot then there must have been something there that grub overwrote. Removing grub probably won't fix it. If Ubuntu can see the file there there is probably a way for Ubuntu to nuke it. Is the partition Mac format? I don't know the status of write support on a Mac FS but there is now supposedly good support for NTFS writing so maybe there is for Mac too. If so, you could delete it but I'm thinking there must need to be something in it's place.

To be honest, I don't have a clue how to fix this. However, since you can read the OSX partition, why not copy all the important stuff, and reinstall. Fixing it would be more rewarding so you might just hang tight and see if anyone else can offer any suggestions. I'll do some checking too and see if I can up with anything.

---

### Post by ZodiacfreaK on 2007-05-12
allright, I do have read write support on the Mac OS partition, it is formatted in HFS+. Last time I had to start from scratch on my mac os partition I had all the files backed up but when I copied them back over I just couldn't get everything to play nice, oh well I'll see what I can do. I'll backup the important stuff and then try to remove the grub files, I doubt that it will solve anything though ;)

---

### Post by ZodiacfreaK on 2007-05-12
Alright now I am getting annoyed :) how can I backup my Mac OS partition to a folder on my other partition!! I already have my OS X partition mounted with read/write.

---

### Post by m.musashi on 2007-05-12
Do you want to back up the entire partition or just the important files? If you back up the whole partition you probably won't solve anything as it will just write the partition back as is and you will be right back where you started. Since the system files and such don't need to be saved (some preferences might if want them), it would be easier to just save the irreplaceable files. To do that, make a folder in either /home or another partition to which you can write and just copy the files.

If you really want to copy the whole partition, I'm not sure what exists for hfs+. I know there are some tools to copy a ntfs partition so something for hfs might exist too. You could also check into dd. That's what it's called - dd. I've never used it but I've heard people use it to copy a whole partition. There is also partimage which is similar. Again, I don't know if any of these work with hfs but they might. It's a place to start.

---

### Post by ZodiacfreaK on 2007-05-13
wow I have absolutely no idea  what is going on now. Apparantly the "files" that I found earlier weren't really there at all, there was a file in their that linked to the linux root partition, wierd. Whenever I get some time I will just erase the partition and re-install everything. I am going to document it step by step, in case this happens again.

---

