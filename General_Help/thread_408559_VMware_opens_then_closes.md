---
title: "VMware opens then closes"
date: 2007-04-13
forum: General Help
---

### Post by garymc1 on 2007-04-13
hi there I installed VMware using the following command

sudo aptitude install linux-headers-`uname -r` build-essential xinetd
wget -c [http://download3.vmware.com/software/vmserver/VMware-server-1.0.2-39867.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.2-39867.tar.gz)
tar xzf VMware-server-1.0.2-39867.tar.gz -C /tmp
cd /tmp/vmware-server-distrib
sudo ./vmware-install.pl

I Accept all defaults and enter my serial.

It is listed in 
Applications -> System Tools -> VMware Server Console

But when I click on it to open it flashes up then closes again 

Thanks Gary

---

### Post by tgm4883 on 2007-04-13
start it from the terminal so you can see any error messages

---

### Post by garymc1 on 2007-04-13
when I open the terminal and type vmware I get the following message

garymc@garymc-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

---

### Post by Error47 on 2007-04-13
Hey I was going through a similar problem, check out my [post]("http://ubuntuforums.org/showthread.php?t=406399").

Right now, when I type vmware in my console, I get that same message, but vmware still opens up. Did you try running ' sudo /usr/bin/vmware-config.pl ' . Sometimes I had to run that to get it working.

---

### Post by tgm4883 on 2007-04-13
Seems this problem is fixed with this

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
```

And if you have problems with running just vmware (and have to run sudo vmware) do this
> sudo chown -R yourusername:yourusername .vmware

All from this thread 

[HTML]http://ubuntuforums.org/showthread.php?t=183209[/HTML]

---

### Post by garymc1 on 2007-04-13
just tried

sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/

but its just the same 

and tried the command
sudo chown -R garymc:garymc.vmware

---

### Post by Error47 on 2007-04-14
What happens when you type ' sudo /usr/bin/vmware-config.pl ' ?

---

### Post by garymc1 on 2007-04-14
when I type ' sudo /usr/bin/vmware-config.pl '
This is what I get then I go through and Accept all defaults and enter my serial


Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons]

---

### Post by Error47 on 2007-04-14
Just accept all the defaults (Press Enter), and it should be re-configured. Does that work?

---

### Post by garymc1 on 2007-04-15
No when I accept all the defaults by pressing (Press Enter) 

It is listed in
Applications -> System Tools -> VMware Server Console
but when i click on it 
it just opens in the bottom panel (like when you minimise something it goes to the bottom of the screen) then it just goes away
Thanks for your help Gary

---

### Post by UltraM4n on 2007-04-17
Hi there. I've been having the same problems as you. I noticed that the Process list shows it as running...so its just  a problem with the program displaying..

---

