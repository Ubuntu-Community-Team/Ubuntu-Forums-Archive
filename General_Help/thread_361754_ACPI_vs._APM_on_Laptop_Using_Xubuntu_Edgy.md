---
title: "ACPI vs. APM on Laptop Using Xubuntu Edgy"
date: 2007-02-14
forum: General Help
---

### Post by Benitez on 2007-02-14
[SIZE="3"]
OK everyone... I assume you've all read the title of the post. I am making the (possibly incorrect) assumption that both ACPI and APM are both being used and supported in my Xubuntu Edgy system. I am running Xubuntu on an old Dell Latitude C610 laptop.

The reason I am posting this is because I had a few problems with getting the laptop lid to successfully suspend or hibernate. Basically the X server would restart and kill the previous session I had running. Nevertheless, I solved the issue with some help on the forums.

Previous to this problem was the installation of Xubuntu Edgy from both an Alternate and Regular CDs. The installer would get stuck while copying the *.deb files from the CD; the solution was to disable APM and ACPI during the install (IIRC, I had to type in **noapic nolapic** in order to do this).

Also, I recently took a look at **[Dell laptop page]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell")**, and wondered if the section refering to the Dell Latitude C600 at the bottom could also refer to me and my laptop. Referring to the subsections where APM vs. ACPI features usable in *buntu, I am able to get some of the Fn + (Key) combinations to work, suspend and hibernate both work correctly, power button press brings a menu to choose method of shutdown or restart and all that. However, I don't know if my machine is being shutdown nicely, I cannot use Fn + F1 to access the BIOS, and I'm unsure if frequency scaling works. 

So now that that's over, which system is best for a laptop like this, or is this a moot question? I know that APM is an older system and ACPI is more full-fledged and newer, but what advantages can either provide me (other than integration with some nice tools such as **gnome-power-manager** and such?

Sorry for such a long, *long* post.

--Benitez
[/SIZE]

---

### Post by kerry_s on 2007-02-14
noapic nolapic does not turn of acpi or apm. There system controls for shared resources.(short story)

both acpi and apm are installed and your system will use the one that is supported. Chances are if your system is newer you don't have apm so your probably using acpi.

Your system is a pentium3-m? Check to see if the "powernowd" is installed using synaptic(menu>system>synaptic)

---

