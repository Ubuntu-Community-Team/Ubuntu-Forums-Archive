---
title: "How to troubleshoot a system that freezes up?"
date: 2008-04-17
forum: General Help
---

### Post by terminaldogma on 2008-04-17
Hello, I am fairly new to linux but i know enough to get myself in trouble (sometimes).  I'm running ubuntu 7.10 on an amd 64 x2 cpu with an 8800GT.  Things generally work quite well...but several times a day i get a total lock-up, screen / cursor / hard drive, it just dies with no error messages.

I have thought of a number of culprits (NVIDIA drivers + my card, firefox, drivers, apic / acpi), but i have not been able to resolve this.  I'm pretty much stuck with my video card, i think firefox has been open on all / most of the lock-ups, even if it is not the active window, i have blacklisted some possibly troublesome drivers for things i'm not using (wifi), and i'm booting with noapic nolapic noacpi).

My question isn't "omg whats wrong here", but what exactly is the method for tracking down what the problem is?  I've gone through /var/log/messages but i have yet to see anything at the time of the problem that shows a clear issue.  Is there anything i can look at or run to at least get an idea of what's going on?

Thanks.

---

### Post by tvtech on 2008-04-17
I had a similar problem but I don't think it's related.  my processor was slowly cooking itself to death and would choke on even the very basic of basic operations.     It's since died

---

### Post by fjgaude on 2008-04-17
I'd first run the memory test at the GRUB menu, and make sure it is solid.

These kinds of failures you are going through can be either software or hardware. Since you are using other than a Beta release of Ubuntu I'd look to hardware.

Things like Firefox are solid in version 2.0. The 3.0 is still in Beta.

When you have a hard crash the logs likely aren't updated quick enough to catch what might have happened.

I trust you are not overclocking your computer?

---

