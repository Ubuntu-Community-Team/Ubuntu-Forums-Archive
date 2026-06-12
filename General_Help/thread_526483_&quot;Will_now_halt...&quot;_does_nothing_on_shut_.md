---
title: "&quot;Will now halt...&quot; does nothing on shut down"
date: 2007-08-15
forum: General Help
---

### Post by Johnny K on 2007-08-15
I have a dual boot set up. Ubuntu starts and runs fine, but will not shut down. When I shut down,  everything is unmounted fine, but then the message "Will now halt..." is displayed and nothing happens. I know this question has been asked before but haven't found an answer in my searching.

My Dell's BIOS looks like this, if it means anything:
Primary Drive 0: 18GB Hard Drive *(100% NTFS, includes Windows)*
Primary Drive 1: 120GB Hard Drive *(Partitioned, ~50GB NTFS and ~70GB ext3 with Ubuntu)*

I read somewhere that it could be an ATI issue. Is that possible and if so would installing fglrx help?

TIA :)

---

### Post by moore.bryan on 2007-08-15
*when you type ```
sudo shutdown -hP now
``` from a terminal, does it shutdown and poweroff?*

---

### Post by Johnny K on 2007-08-16
Nope.

Instead of getting the "Will now halt..." message though, I just get a black screen and a flashing underscore at the top left. It doesn't go away. The machine has to be powered off manually at that point.

---

### Post by moore.bryan on 2007-08-16
*okay... does ```
sudo poweroff now
``` do anything from the terminal?*

---

### Post by UK-Wobbie on 2007-08-16
> **Johnny K said:**
> I have a dual boot set up. Ubuntu starts and runs fine, but will not shut down. When I shut down,  everything is unmounted fine, but then the message "Will now halt..." is displayed and nothing happens. I know this question has been asked before but haven't found an answer in my searching.

My Dell's BIOS looks like this, if it means anything:
Primary Drive 0: 18GB Hard Drive *(100% NTFS, includes Windows)*
Primary Drive 1: 120GB Hard Drive *(Partitioned, ~50GB NTFS and ~70GB ext3 with Ubuntu)*

I read somewhere that it could be an ATI issue. Is that possible and if so would installing fglrx help?

TIA :)

Thats funny lol I keep getting the same msg! When you power off it sometimes say ((Will now halt..))

But it says that at the last thing on the screen so i no it's ok to turn off!
You be ok on turning it off dude! All it is Ubuntu being gay on not turning off lol :)

---

### Post by UK-Wobbie on 2007-08-16
> **Johnny K said:**
> I have a dual boot set up. Ubuntu starts and runs fine, but will not shut down. When I shut down,  everything is unmounted fine, but then the message "Will now halt..." is displayed and nothing happens. I know this question has been asked before but haven't found an answer in my searching.

My Dell's BIOS looks like this, if it means anything:
Primary Drive 0: 18GB Hard Drive *(100% NTFS, includes Windows)*
Primary Drive 1: 120GB Hard Drive *(Partitioned, ~50GB NTFS and ~70GB ext3 with Ubuntu)*

I read somewhere that it could be an ATI issue. Is that possible and if so would installing fglrx help?

TIA :)

I tell you this :) It's not a ATI issue it's UBUNTU it self lol I have got a Nvidia in my Computer and it works ok.. And Beryl works ok.. It's Ubuntu you may Instill something what as made it go like this or it may Ubuntu being a b lol :)

---

### Post by nelamvr6 on 2007-08-16
This is a known issue with Dell computers.  Mine does the same thing.

If you do a search on troubles powering down or restarting you will be astonished at how many of the problem systems are Dells.

There was a proposed work-around that involved inserting a Reboot=R statement, it kinda worked for me, but not all the way.

As of right now my system shuts down most of the time but won't restart at all.

---

### Post by moore.bryan on 2007-08-16
*my thinkpad has issues shutting-down as well and it turned-out to be a script in /etc/rc0.d that shouldn't have been there.  could you post the files in that dir?*

---

### Post by justinw28 on 2007-08-16
Same thing happens on my hp dv202ca laptop with an nvidia card.  The problem is more frequent when restarting than shutting down.

---

### Post by Johnny K on 2007-08-16
Thanks for all the help, moore.bryan's!

***sudo poweroff now*** leaves me with the flashing underscore just like ***sudo shutdown -hP now*** does.

These are all the files in /etc/rc0.d (I also have a tar of the directory, if that would be of any use):
```
K01gdm      K25hwclock.sh                       S15wpa-ifupdown  S40umountfs
K01usplash  K50alsa-utils                       S20sendsigs      S60umountroot
K19hplip    README                              S30urandom       S90halt
K20apport   S01linux-restricted-modules-common  S31umountnfs.sh
```

---

### Post by moore.bryan on 2007-08-16
[I]no problem...

yeah, post the tar and i'll have a looksee...[/I]

---

### Post by Johnny K on 2007-08-16
Here ya go.

---

### Post by moore.bryan on 2007-08-17
[I]okay.  let's try a symlink to shutdown your local scripts... i don't know why it's not there now.
```
sudo ln -s /etc/init.d/rc.local /etc/rc0.d/K01rc.local
```
and try a shutdown with
```
sudo shutdown -hP now
```[/I]

---

### Post by Johnny K on 2007-08-17
After doing ***sudo ln -s /etc/init.d/rc.local /etc/rc0.d/K01rc.local***, both ***sudo shutdown -hP now*** and ***sudo poweroff now*** left me with the flashing underscore. The normal GUI shutdown left me with the "Will now halt..." message.

I guess there isn't much that can be done. Is it at least safe to manually power it off once it gets to either the "Will now halt..." message or the flashing underscore?

---

### Post by moore.bryan on 2007-08-17
*no, turning it off at that point is fine... it's just strange that it's doing it.*

---

### Post by Johnny K on 2007-08-17
Alright, good to know.

Thanks for all the help! Should I file a bug report in Launchpad or something?

---

### Post by UK-Wobbie on 2007-08-17
> **nelamvr6 said:**
> This is a known issue with Dell computers.  Mine does the same thing.

If you do a search on troubles powering down or restarting you will be astonished at how many of the problem systems are Dells.

There was a proposed work-around that involved inserting a Reboot=R statement, it kinda worked for me, but not all the way.

As of right now my system shuts down most of the time but won't restart at all.

My Computer is not a Dell lol So it's not a Dell issue!...I no what you mean on Dell computers..
I made my computer my self :)

I say it's got something to do with Ubuntu it self! Like a bit of a bug or something you instilled on some update!
What may have put something in the turn off code!

---

### Post by moore.bryan on 2007-08-17
[I]none of it makes sense... it could just be a process hanging or something.

do you both have nvidia, by any chance?[/I]

---

### Post by Bachstelze on 2007-08-17
It's a verry common issue, just buggy ACPI. If you want, you can have a look [here](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems).

---

### Post by UK-Wobbie on 2007-08-17
> **moore.bryan said:**
> [I]none of it makes sense... it could just be a process hanging or something.

do you both have nvidia, by any chance?[/I]

Process hanging? You mean code stopping? :)

Yer i do have a nvidia card but that as not got anything to do with this lol 
I had this be for i put my card in to my PC :)

---

### Post by moore.bryan on 2007-08-17
> **HymnToLife said:**
> It's a verry common issue, just buggy ACPI. If you want, you can have a look [here](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems).
*you'd think with something as basic as acpi, someone would have squashed this bug...*
> **UK-Wobbie said:**
> Process hanging? You mean code stopping? :)

Yer i do have a nvidia card but that as not got anything to do with this lol 
I had this be for i put my card in to my PC :)
[i]code stopping/script running/processes... you say poe-tay-toe, i say poe-tah-toe.  ;-)
i've just seen this so many times with people who use nvidia, it's bizarre coincidence.
[/i]

---

### Post by UK-Wobbie on 2007-08-17
> **moore.bryan said:**
> *you'd think with something as basic as acpi, someone would have squashed this bug...*

[i]code stopping/script running/processes... you say poe-tay-toe, i say poe-tah-toe.  ;-)
i've just seen this so many times with people who use nvidia, it's bizarre coincidence.
[/i]

But it's funny how i use to get it when i did not have my nvidia in my pc :confused: And the guy who Put this topic down as got a ATI Card or some one put something like that :confused:
I still say it's something in Ubuntu...

I made my pc my self and at the start of things it was working ok... It turns off ok and starts ok! But then i do not no if some updates or something i instilled as done something :confused: But sometimes it use to do the  "Will now halt..."  thing lol And now i put my card in it still do it lol :confused:

---

### Post by Bachstelze on 2007-08-17
> **moore.bryan said:**
> *you'd think with something as basic as acpi, someone would have squashed this bug...*

If you had read the link I posted, you'd have see the bug does not reside in Ubuntu's ACPI code but in the machine's DSDT, and this is something only the manufacturer can fix. And asking Linux-related fixes to most manufacturers is like asking RMS to buy an iPhone.

---

### Post by UK-Wobbie on 2007-08-17
> **HymnToLife said:**
> If you had read the link I posted, you'd have see the bug does not reside in Ubuntu's ACPI code but in the machine's DSDT, and this is something only the manufacturer can fix. And asking Linux-related fixes to most manufacturers is like asking RMS to buy an iPhone.

So your saying that linux Ubuntu can not go on some Computers in away?
And we are pushing Ubuntu on to it lol

---

### Post by moore.bryan on 2007-08-17
> **HymnToLife said:**
> If you had read the link I posted, you'd have see the bug does not reside in Ubuntu's ACPI code but in the machine's DSDT, and this is something only the manufacturer can fix. And asking Linux-related fixes to most manufacturers is like asking RMS to buy an iPhone.
*from your original post, it sounded as if you were citing a site which detailed why/how it was an acpi issue... sorry if i misunderstood.:oops:*

---

### Post by Johnny K on 2007-08-20
> **moore.bryan said:**
> [I]none of it makes sense... it could just be a process hanging or something.

do you both have nvidia, by any chance?[/I]
ATI

---

### Post by moore.bryan on 2007-08-21
> **Johnny K said:**
> ATI
*that does make it odd....*

---

### Post by TrevorNC on 2007-08-27
I believe that I may have the solution to this problem.

I was experiencing exactly the same problem as described in this thread on an old Gateway machine on which  I had just installed Feisty.

The resolution was to specify acpi=force as part of the boot command. I suspect that the reason that this is a problem in Feisty is that it automatically switches off acpi functionality when a bios is dated older than 1999.

On boot, press ESC to go to the grub menu.
Press 'e'  to edit the appropriate boot up command.
Highlight the line beginning with kernel and press 'e' again.
Add 'acpi=force' without the quotes to the end of the line, press enter, then press 'b' to boot using the updated command.

To enable this change permanently edit the boot command in /boot/grub/menu.lst

Hope this solves this problem for you.

Trevor

---

### Post by sblanzio on 2007-08-29
Well, I think this problem is not solved for me...

Unluckily I have to disable acpi due to a boot problem. In fact, if I don't switch off the acpi I even can't load ubuntu.

Now, when I shutdown it completes all its tasks and then says "Will halt now" but nothing happens, until I press the power switch, obviously.


Is there any other way to walk?

---

### Post by nikef on 2007-08-29
Hi all
i get the same problem,on shut down it shows a lot of txt,it is stopping the sevices 
it cant be a manufacturing falt as we would also get the same problems when windoze was installed :confused:

---

### Post by meharts on 2007-10-22
Hi to everyone. I have the same shut down problem, although TrevorNC's answer worked for me for the last version of ubuntu? I tried adding acpi=force this time and nada!!

Why can't ubuntu solve such stupid issues. I came over to ubuntu to try the server, but I think I will go back to clarkconnect. Clarconnect don't have a problem shutting down my dell?!

Even though I have added acpi=force I get the following error:

> 

halt: unable to iterate IDE devices: no such file or directory [238.999406] system halted



What else are we supposed to do to make the computer shut down properly?!!

meharts

---

### Post by sblanzio on 2007-10-22
I know this is not much, but you could feel worse...

In feisty I could boot just with "acpi=off" option, and I couldn't halt the computer automatically.

Gutsy doesn't boot at all, even with acpi=off.

As I already said elsewhere, i think this is a acpi backward step.

---

### Post by UK-Wobbie on 2007-10-22
I use to get this  "Will now halt..." does nothing on shut down.. On Ubuntu 7.04 but on Ubuntu 7.10 it as stopped :)

---

### Post by meharts on 2007-10-22
Hi guys, I have a new twist to the whole situation. Like I pointed out before I just needed to add acpi=force to the boot grub menu.list - well, have to tell you something ( no laughing mind) I had recently run clarkconnect without power down problems  - I had acpi turned off in bios but it all worked.

I can hear somebody laughing!! Anyway, I turned it on again and edited the boot grub menu.list how TreverNC explained and booted into the distro. The first thing I did after logging in as root was the "shutdown - h now" command and my computer completely shut down.

Are you keeping up? Well, I restarted the computer and after logging in as root I tested the "shutdown -h now" command again and .........nada?!!

I rebooted and checked the boot grub menu.list and there was no entry for acpi=force? I re-entered the info and went through the whole process again and again. Every time I entered the info as TrevorNC explained it wasn't saved until the next boot?" I even checked the file to make sure I was saving it right - no problem but disappeared after the first shutdown?

I am running the server version of ubuntu, so I use webmin as my gui. When I started the computer and edited my boot grub file again I  continued and checked the info in webmin through the file manager. Guess what - no entry for acpi=force?

I edited the file with webmin in file manager and saved and closed file manager. I used the "bootup and shutdown" in webmin and my computer shutdown as usual.

I have now tested that several times and no problem!! There must be something wrong with editing that file from boot up? Those of you not using the server version or webmin can edit the file in upbuntu with one of the text editors.

I hope that is of help to someone!!

meharts

---

### Post by sblanzio on 2007-10-22
> **sblanzio said:**
> I know this is not much, but you could feel worse...

In feisty I could boot just with "acpi=off" option, and I couldn't halt the computer automatically.

Gutsy doesn't boot at all, even with acpi=off.

As I already said elsewhere, i think this is a acpi backward step.

I'm sorry.. These problems was by my fault.
Here it's described why.
[http://ubuntuforums.org/showpost.php?p=3599641&postcount=8](http://ubuntuforums.org/showpost.php?p=3599641&postcount=8)

my apologyses
bye!

sblanzio

---

### Post by ThomThom on 2007-10-28
I've got an Via EPIA SP 13000 and I also had problems where after the shut down progressbar had finished the screen just stayed there.

If I disabled the screen I got this message:
> 
---
 System is shutting down, please wait...
---

NetworkManager: <WARN>  mn_signal_handler(): caught signal 15, 
shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1193573771.092816] nm_print_open_socks() 
Open sockets List:

NetworkManager: <debug> [1193573771.092816] nm_print_open_socks() 
Open sockets Done.

NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - 
Did not receive a reply. Possible causes include: the remote 
application did not send a reply, the message bus security policy 
blocked the reply, the reply timeout experied, or the network 
connection as broken.

[  226.137045] System halted.



I noticed that when I booted I saw something saying "no DMI BIOS year, acpi=force is required to enable ACPI"

From what I gather, BIOSes from before 2000 will cause ACPI to not load, right? The BIOSes availible from VIA is all from 2005; [http://www.via.com.tw/en/products/mainboards/downloads.jsp?motherboard_id=261](http://www.via.com.tw/en/products/mainboards/downloads.jsp?motherboard_id=261)

But seeing that it complained about not finding "DMI BIOS year" I guess that the BIOS is missing some info in regards to identifying itself. Or is it the bootloader/kernel/orwhateveritmightbe that doesn't read the BIOS correctly?

Adding acpi=force made my system shutdown correctly.

---

