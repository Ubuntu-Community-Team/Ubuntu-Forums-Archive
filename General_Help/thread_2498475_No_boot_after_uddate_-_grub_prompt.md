---
title: "No boot after uddate - grub prompt"
date: 2024-06-15
forum: General Help
---

### Post by leejenon on 2024-06-15
```
plex@Mini-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
plex@Mini-PC:~$ sudo dmidecode -s bios-version
GK1V26C01
plex@Mini-PC:~$ grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2

```

HI, after an update I am unable to boot. Please see screen shots. In summary I get two prompts at the GNU GRUB screen. When I select Ubuntu I can choose an instance. This boots ok. If I then reboot, the PC hangs at the 'or <ESC> to enter setup.' screen. I then need do a hard reboot to get back to those two prompts.

Any suggestions please?

Thanks, Lee

---

### Post by tea for one on 2024-06-15
> **leejenon said:**
>  I then need do a hard reboot to get back to those two prompts
If you power off/power on (i.e. hard reboot), while your ESP is mounted, you can sometimes end up with file system damage.

First of all, I would boot into a "Try Ubuntu" live session and check the file systems, using fsck.
Are you familiar with this procedure?

---

### Post by Rubi1200 on 2024-06-15
I would also recommend booting a live USB and choose to Try Ubuntu.

Then run the boot repair script in my signature. Do not try to repair but choose the option to create a summary report with a pastebin link.

You can then post that link here so we can review and see what is what.

---

### Post by leejenon on 2024-06-16
Hi both,

I can boot up when I select Ubuntu and then a Ubuntu instance from the list. Not sure what a live session is?

I'll run the file system command and the script. I'll be back.

---

### Post by tea for one on 2024-06-16
> **leejenon said:**
>  Not sure what a live session is?
Really - or are you just being playful?
I'm happy to play.
Pop these three words into your favourite search engine and see what transpires?
> live session Ubuntu

---

### Post by leejenon on 2024-06-19
> **tea for one said:**
> Really - or are you just being playful?
I'm happy to play.
Pop these three words into your favourite search engine and see what transpires?

:) - not playing - I just hadn't looked it up when I was last here. I understand now. I am just running these scripts - brb 

Lee

---

### Post by leejenon on 2024-06-19
HI, Please see attached files as requested -

When I try to upload the system-info file, it says 'invalid file'. Attached is the other one 'Boot-Info_20240619_1750.txt'

Lee

---

### Post by leejenon on 2024-06-24
> **Rubi1200 said:**
> I would also recommend booting a live USB and choose to Try Ubuntu.

Then run the boot repair script in my signature. Do not try to repair but choose the option to create a summary report with a pastebin link.

You can then post that link here so we can review and see what is what.

I have run the repair option for the Boot script. The details are here -

[https://paste.ubuntu.com/p/WnVtDVpxBB/](https://paste.ubuntu.com/p/WnVtDVpxBB/)

The boot issue still occurs. Can I have some guidance please? I am not familiar with Linux, so need help navigating please :)

Lee

---

### Post by tea for one on 2024-06-24
You have run the boot-repair report from your installed system, therefore Ubuntu does boot eventually.
I notice that you have 3 other disks attached when you boot.

As an experiment, power off the PC
Remove sdb,sdc, and sdd
Power on and boot.

Any improvement?

---

### Post by leejenon on 2024-06-24
Hi, I unmounted the 3 external disks, switched them off, & restarted, but I still get the grub prompts.

Lee

---

### Post by tea for one on 2024-06-24
Leave your other disks unavailable.
At the grub prompt, type exit
What do you see?

---

### Post by leejenon on 2024-06-24
If I press 'e' for exit at the grub screen it lists various config entries. If I press ESC, the computer hangs with no keyboard lights.

See screen shot attached.

Lee

---

### Post by tea for one on 2024-06-24
'e' is for edit
At grub prompt, please type exit and hit the enter key.

---

### Post by leejenon on 2024-06-24
If I select 'c' for command prompt I get the attached...If I then type exit - just a cursor appears. If press enter, it reboots.

---

### Post by tea for one on 2024-06-24
After booting, please show a picture of your first grub screen

---

### Post by leejenon on 2024-06-24
See attached -

---

### Post by tea for one on 2024-06-24
Scroll down to the second line, hit enter - can you show another picture?

---

### Post by leejenon on 2024-06-24
Choosing the second option causes a reboot. I then get back into an instance by selecting the second one from the bottom of the list. See attached -

---

### Post by tea for one on 2024-06-24
Please select kernel 6.5.0-41-generic and hit enter.
Successful boot?

---

### Post by leejenon on 2024-06-24
Yes, it boots successfully. A reboot behaves the same also after selecting it. Grub prompt.

---

### Post by tea for one on 2024-06-24
The first grub option displays a kernel with an unusual nomenclature - 6.5.0-342405280420-generic
Where did it come from?

We can arrange grub to priority boot 6.5.0-41 if you wish?

---

### Post by leejenon on 2024-06-24
No idea where it came from. It's always been there since I had the problem. Maybe before - not sure.

Oh, that would be great if we can boot that version.

---

### Post by tea for one on 2024-06-24
Grub counts from 0 hence GRUB_DEFAULT=0 is the first line of the Grub menu, which will boot the latest installed kernel.
GRUB_DEFAULT="[COLOR="#0000FF"]1[/COLOR]>[COLOR="#FF0000"]2[/COLOR]"
The 1 in blue is the second line of the Grub menu i.e. Advanced Options for Ubuntu.
The 2 in red is the third option from the second line i.e the previous kernel.
Don’t forget to run sudo update-grub after editing the file.
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT="1>2"
```
```
sudo update-grub
```
Also, you may wish to start a new thread with the object of deleting the unusual kernel.

---

### Post by leejenon on 2024-06-24
Oh, I see, so it's trying to boot a version with a weird kernel increment.

I changed the file - 
```

GRUB_DEFAULT="1>2"
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

I also did this - 

```
plex@Mini-PC:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-342405280420-generic
Found initrd image: /boot/initrd.img-6.5.0-342405280420-generic
Found linux image: /boot/vmlinuz-6.5.0-41-generic
Found initrd image: /boot/initrd.img-6.5.0-41-generic
Found linux image: /boot/vmlinuz-6.5.0-35-generic
Found initrd image: /boot/initrd.img-6.5.0-35-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done
plex@Mini-PC:~$ 
```

Restarted

...but it is still stopping at the grub prompt.

Lee

---

### Post by tea for one on 2024-06-24
Is it the same malformed screen attached to post 16?

---

### Post by leejenon on 2024-06-24
Yes

---

### Post by leejenon on 2024-06-24
I am wondering if I create that other thread about those kernels. Remove  them and set that attribute back to "0" it may help?

---

### Post by leejenon on 2024-06-24
I have to go now. I'll get back on this tomorrow. Thanks for your time. Lee

---

### Post by tea for one on 2024-06-24
When you boot the PC and the malformed grub screen appears, hit the enter key.
I hope that this will now boot into kernel 6.5.0-41-generic?

---

### Post by leejenon on 2024-06-24
I just read your reply and realised I didn't wait for the count down to finish. It then boots into 6.5.0-41.

Thanks for all your help, I've learnt a lot today.

Lee

---

### Post by bergasha on 2024-07-09
I had the exact same issue as OP and joined just to say thank you this fixed my issue also.

---

