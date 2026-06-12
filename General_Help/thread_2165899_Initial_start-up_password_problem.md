---
title: "Initial start-up password problem"
date: 2013-08-06
forum: General Help
---

### Post by mike64485 on 2013-08-06
I hope someone can help this old man, I just installed Ubuntu _10.04_ LTS on
an older Dell Inspiron desktop. I entered my new password, pushed 'enter' ... 
and instantly forgot what I had just typed. A classic 'senior moment'.

I googled 'lost password in Ubuntu 10.04' and got some hits on how to RESET 
a p/w using grub boot menu or using the 'shift' key on boot, but these methods don't 
work on my new installation.


Will someone please help me recover or reseet my password.

Thanks in advance.

Mike

---

### Post by Bashing-om on 2013-08-06
Mike, Not a problem...
however, 10.04 has reached End Of Life. It no longer enjoys any support for the desktop edition. One is strongly urged to install a current version ..12.04, the current LTS version, has support 'till 2017.

To reset ones password, follow this tutorial:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mike64485 on 2013-08-06
[ 						 							]("http://ubuntuforums.org/member.php?u=1111508")[[COLOR=#000000]Thanks, Bashing-om[/COLOR]]("http://ubuntuforums.org/member.php?u=1111508"), but I tried that solution and got no satisfaction.
Is there something special about the initial boot of a system that 
prevents grub menu from showing up until the p/w is first entered?

As for using 10.04, that is a personal decision based on my dislike
for the newer versions. I have used LL since it came out and why
change. Heck, my pick-up truck is more than 20 years old and 
meets all my needs!

But that's a different discussion.

Mike

---

### Post by deadflowr on 2013-08-06
There's a trickiness to getting the grub menu on a single OS system.
It usually involves a level of timing.
Press down on shift when the BIOS screen dissappears and let go as soon as you see the grub loading come up.

Another option is to forgo that and just use a liveCD to recover
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by Bashing-om on 2013-08-06
Mike,
See deadflower's last... iffen ya still having problems ... holler back .. I have a couple other methods up my sleeve.
As to old ways ... hummm ... MY PickUp is a 1981 model ... purchased in 1982 ... solid as an Arkansas field stone.

As to updating ... try a minimal install and use xfce4 for the desk top environment .. simple, fast and handy !
I was impressed with unity ... found I really liked it after I got acclimated to it ... but I value simplicity more . - no bloat, no fuss and no muss.

[INDENT][INDENT]hey, it's worth a thought
[/INDENT][/INDENT]

---

### Post by mike64485 on 2013-08-06
[**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577"), [**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508") 

I guess my timing isn't as good as it used to be, 'cause 
i still can't see the boot menu. I saw it every time on earlier 
installs, but not this time. I think the custom Dell branding
that shows up on-screen blocks the view of the bios screen.
I've about worn out my start switch, I think.

Mother-of-my-children will want her laptop back soon. It is Windows.
Uggggghhh!  
(Our 40th come Monday)





Mint ... hmmmm.

Mike

P.S.  Live CD wanted a password to boot, even after 
I selected CD/DVD as my first boot device.  Bummer.
I really don't understand that.

---

### Post by Bashing-om on 2013-08-06
Mike .. that puts me in mind that BIOS is what is password protected !
Check your bios and if required .. reset it to factory defaults to loose that requirement .. if indeed BIOS is password protected ...

[INDENT][INDENT]just another thought
[/INDENT][/INDENT]

---

### Post by mike64485 on 2013-08-07
Just tried resetting bios; got into bios with f2, and selected f9, f10, 
as directed by the bios screen to reset. Stupid computer then booted 
into Ubuntu and asked me for my p/w.

Since I know the general form of my password I had my daughter 
work a truth table of all the combinations that don't involve misspelled 
parts. I will try 'shift' on boot for a while, and then go to 
brute force this morning if no one has any other suggestions.

At least I have a good back-up disk with all my personal files.

Thanks for the help so far;

Mike

---

### Post by Bashing-om on 2013-08-07
Mike;

Not much one can say ... There is no requirement within 'buntu to boot the liveCD.. I have used some form of 'buntu since version 6.04 ...and have never encountered - nor have I heard of - a situation in booting needing a password. That requirement for a password to boot another OS must be machine specific and must exist within bios ...  Generally, when booting .. bios looks for the boot code on a specific device as you have set as the boot priorities in an option in bios. Bios hands off to the bootloader (grub) and simply put, grub hands off to the kernel to complete the boot process. Prior to a user logging onto the system, there is no need of a password ('buntu).

Maybe, in order to remove that password and revert bios ... one has to remove the battery from the motherboard AND jumper a CMOS chip - This procedure does vary, one should consult the manufactures' documentation when in doubt. To this time I have always been able to find the docs on-line, knowing the motherboards' manufacturer and what bios was installed by the manufacturer.

[INDENT][INDENT]I do hope this helps
[/INDENT][/INDENT]

---

### Post by mike64485 on 2013-08-07
Success! Joy I finally got the right split second bouncing 
the 'shift' key and was able to see the boot menu. Selecting 
recovery mode allowed me to access the root terminal and 
change my p/w to something I can remember.
The problem was the proprietary splash screen from the Dell system 
that covers the  bios screen and boot menu.

Thank you both for your help. I really appreciate it.

Mike

---

### Post by Bashing-om on 2013-08-07
Mike; Glad ya got resolution to this little one ..
onward and upward.

Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Thread Tools drop-down -> Mark thread as solved.

[INDENT][INDENT]look'n forward to "reading" you later
[/INDENT][/INDENT]

---

