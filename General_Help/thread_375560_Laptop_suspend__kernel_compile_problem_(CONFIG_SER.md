---
title: "Laptop suspend / kernel compile problem (CONFIG_SERIO_I8042)"
date: 2007-03-03
forum: General Help
---

### Post by saro on 2007-03-03
I am trying to make suspend work on feisty on my HP NC6400 laptop. The keyboard freezes on resume and according to [http://hpwiki.cactii.net/hpwiki/NC6400](http://hpwiki.cactii.net/hpwiki/NC6400) I need to compile the kernel with I8042 as a module and suspend2 will work.

so I downloaded and copied the config from /boot and changed CONFIG_EMBEDDED=y and CONFIG_SERIO_I8042=m and issued the following command 


```
make-kpkg --rootcmd fakeroot --initrd --append-to-version=saro kernel-image kernel-headers

```

But it did not compile I8042 as a module. When I checked the .config it said CONFIG_SERIO_I8042=y

So I changed it again to "m" reissued the command but still it kept compiling it into the kernel. 

Any pointers how to make it compile as a module ?

thanks,
Saro

---

### Post by Greg_L on 2007-03-28
Did you have any luck with this?

I have the same laptop and just installed Feisty. Suspend/resume works just as you describe. The laptop comes back just fine but keyboard/touchpad don't work so I have to connect an external mouse and keyboard to get it to work.

---

### Post by tareko on 2007-04-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497) for the fix. It involves adding a couple of lines to a file in /etc/acpi/resume.d

tarek : )

---

