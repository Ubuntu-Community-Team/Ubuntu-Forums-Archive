---
title: "Laptop not turning off 100% under Ubuntu (working fine under Windows)"
date: 2021-08-22
forum: General Help
---

### Post by bubbabubbarda on 2021-08-22
Hi all,

I am new to Ubuntu so I don't have idea how this works. I bought a new laptop Lenovo Thinkpad L15 gen2 (11th Gen Intel® Core™ i7-1165G7 @ 2.80GHz × 8, Mesa Intel® Xe Graphics (TGL GT2)) and installed Ubuntu 20.04.3 LTS. My wifi wasn't working so a User of this forum helped me to make it work (used this solution: [https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04](https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04)).

After that whenever I try to turn of the computer, screen turns off, power button light turns off but Num Lock or Caps Lock lights do not turn off and I am not able to turn on the computer anymore. I must press power button for 10 seconds in order to fully turn it off (after those 10 seconds all keyboard lights turn off) and then I am able to turn it on again. This issue is not happening under Windows.

I don't know what might be the problem, but sometimes it doesn't happen if I had closed the cover or suspended the computer, maybe 2 out of 5 times I did that, then I can turn it off normally, but if I don't do that (close cover or suspend) 100% of the times the issue occurs.

This is what I see once I use the Power Off option under Ubuntu and screen and power button light already turned off: [https://imgur.com/a/PZA6kfG](https://imgur.com/a/PZA6kfG)
After that I can't turn on the computer again, I need to press 10 seconds the power button to turn if off 100% and only after that I can turn it on again.

Hope you can help me.

Thanks in advance,

Matias

---

### Post by Portaro on 2021-08-22
You can try run the poweroff command on terminal to see if appear any message.

$ poweroff

You also  can see your system logs on /var/log/syslog

$ cat /var/log/syslog | grep 'Error'

---

### Post by monkeybrain20122 on 2021-08-22
Did you turn off fast boot in Windows?

---

### Post by bubbabubbarda on 2021-08-22
Thank you both for your replies.

@Portaro: Didn't find any error in system logs, all errors are from yesterday and before that, and today I turned off like 30 times or more. Tried by using the poweroff command and like 3 out of 5 is turning off correctly.

@monkeybrain20122: About the fast boot in Windows, do you mean in the Bios? I don't know any fast boot option in Windows, only the Bios one.

EDIT: This is how the option in the Bios is configured: [https://imgur.com/a/JJYGnGi](https://imgur.com/a/JJYGnGi)

If I turn it off in the login screen (without logging the User) it's working fine.

EDIT 2: found this in logs app:
22:33:24 kernel: power_ctrl_logic 0000:00:00.0: @power_ctrl_logic_probe: fail to add gpio
22:33:24 kernel: usbhid 3-1:1.1: couldn't find an input interrupt endpoint
22:33:24 kernel: pci 0000:00:07.0: DPC: RP PIO log size 0 is invalid
22:33:24 kernel: x86/cpu: VMX (outside TXT) disabled by BIOS

---

### Post by him610 on 2021-08-22
> I don't know any fast boot option in Windows
In Windows, it is called Fast Start which can be disabled within Windows.
[https://www.windowscentral.com/how-disable-windows-10-fast-startup]("https://www.windowscentral.com/how-disable-windows-10-fast-startup")

---

### Post by bubbabubbarda on 2021-08-22
Thanks for your reply. I already disabled fast start and also disabled hibernate (to also gain some free space by not having the hiberfile.sys) but under Ubuntu I am still facing the issue.

If there is anything you know I can try, I'd appreciate it.

Cheers,

Matias

---

### Post by tea for one on 2021-08-23
> **bubbabubbarda said:**
>  I bought a new laptop Lenovo Thinkpad L15 gen2 (11th Gen Intel® Core™ i7-1165G7 @ 2.80GHz × 8, Mesa Intel® Xe Graphics (TGL GT2)) and installed Ubuntu 20.04.3 LTS. 

11th Gen Intel is quite new.
New hardware often functions better with a new kernel.
Perhaps the kernel in Ubuntu 21.04 or Ubuntu 21.10 in development will help?

---

### Post by bubbabubbarda on 2021-08-23
I get what you are saying, thanks for your help, I think I can't do that because I have some requirements from the company I will start working next Monday. I will ask if it is possible to use those versions but I don't think so. Even 20.04 I don't know if I can use. They told me 16.04 or 18.04 so I will ask.Thanks

---

### Post by ActionParsnip on 2021-08-23
If you run:
```

sudo shutdown -h now

```
Does it power off OK?

---

### Post by monkeybrain20122 on 2021-08-23
> **bubbabubbarda said:**
> I get what you are saying, thanks for your help, I think I can't do that because I have some requirements from the company I will start working next Monday. I will ask if it is possible to use those versions but I don't think so. Even 20.04 I don't know if I can use. They told me 16.04 or 18.04 so I will ask.Thanks

You can grab a new kernel from [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13.12/").

Create a folder, give it a name like linux.

download the linux-headers-generic, linux-headers-all, linux-image-generic and linux-modules-generic debs for amd64 and save them in the folder you just created (linux in our example)

then
```

cd linux

sudo dpkg -i *.deb
```

Then reboot. If the new kernel doesn't work. Reboot, press esc to bring up the grub menu, choose advanced option, boot into the previous kernel and uninstall those packages you just installed (it would be really convenient if you have synaptic) I linked you to the latest release but you can try other versions by going to the parent  folder and choose from there.

Edited: if they tell you 16.04 they probably don't know what they are talking about and give you outdated info. 16.04 reached end of life in April.

---

### Post by bubbabubbarda on 2021-08-23
> **ActionParsnip said:**
> If you run:
```

sudo shutdown -h now

```
Does it power off OK?

Tried and no, it does not power off correctly.

---

### Post by bubbabubbarda on 2021-08-23
> **monkeybrain20122 said:**
> You can grab a new kernel from [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.13.12/").

Create a folder, give it a name like linux.

download the linux-headers-generic, linux-headers-all, linux-image-generic and linux-modules-generic debs for amd64 and save them in the folder you just created (linux in our example)

then
```

cd linux

sudo dpkg -i *.deb
```

Then reboot. If the new kernel doesn't work. Reboot, press esc to bring up the grub menu, choose advanced option, boot into the previous kernel and uninstall those packages you just installed (it would be really convenient if you have synaptic) I linked you to the latest release but you can try other versions by going to the parent  folder and choose from there.

Edited: if they tell you 16.04 they probably don't know what they are talking about and give you outdated info. 16.04 reached end of life in April.

Oh ok, didn't know that about 16.04. Anyway, I will wait for onboarding meeting on Friday and I will ask about this problem and maybe they let me update kernel.

Thanks all of you for your help

---

### Post by dkay36 on 2021-12-05
Any Updates on this one?

I handled this problem with deactivating the "hardware support for Lenovo ThinkPad L14 Gen 2, L15 Gen 2 from oem-sutton.simon-aenescumb-meta" within the "Anwendungen & Aktualisierungen" think "Applications & Updates" in english, but now this one don't helps anymore...

I have the same problem like you, [REMOVED SEE EDIT]
  A few times it powers off correctly but most of the times not....

Would be happy if you already found a solution and share it with me :)
[B]
EDIT:[/B] [REMOVED: logged in user can't power off correctly without log in it works.] ->shutdown also dont works everytime when logged out.

---

### Post by bubbabubbarda on 2021-12-07
> **dkay36 said:**
> Any Updates on this one?

I handled this problem with deactivating the "hardware support for Lenovo ThinkPad L14 Gen 2, L15 Gen 2 from oem-sutton.simon-aenescumb-meta" within the "Anwendungen & Aktualisierungen" think "Applications & Updates" in english, but now this one don't helps anymore...

I have the same problem like you, [REMOVED SEE EDIT]
  A few times it powers off correctly but most of the times not....

Would be happy if you already found a solution and share it with me :)
[B]
EDIT:[/B] [REMOVED: logged in user can't power off correctly without log in it works.] ->shutdown also dont works everytime when logged out.

Hi, I didn't find any solution but I stopped looking for it like 2 months ago or more. At the place I started working they let me use Windows so I installed Win10 and no more issues. I'll close this thread. Thanks

---

