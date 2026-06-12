---
title: "multiple issues appeared in past few days"
date: 2016-04-21
forum: General Help
---

### Post by stephen98 on 2016-04-21
Hi, a few days ago I noticed several strange things happening. I noticed flash crash on BBC iplayer - I could not get it to start  properly even after re-installing - it will load, but when you press  play it crashes instantly. The Adobe Flash check page says everything  looks good. Since then I have also noticed that all images on Firefox  are appearing corrupted - see attached Lionel Richie

  Original image:  [http://media.ticketmaster.co.uk/tm/en-gb/dbimages/55400a.jpg](http://media.ticketmaster.co.uk/tm/en-gb/dbimages/55400a.jpg)

  In addition, Chrome has stopped working all together (it was working  perfectly before this) - deleting and re-installing does not help.

  However, I can get it to work **once** by reinstalling  unity. When Chrome is working, I get the same image and Flash issues I  get in Firefox. When I close Chrome, it will not open again - **unless** I re-install unity again , that is.

  To re-install unity I did:
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```  Though as mentioned previously, this only lets Chrome run once before it stops working again.
  Some details on my graphics card (though not convinced its graphics card related)
```
  sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:3000(size=64)

```     
I have done a memory check, disk check, motherboard check, done an antivirus scan - all passed with no issues

I Also tried installing ubuntu  on a different partition - but getting same issues - in-fact images were  corrupted on the install screen, and it was loading from an iso on a usb  stick 

more recently i'm getting ssl issues - I have to load any ssl page several times before it works and when trying to ssh onto a separate server im getting bad mac address errors

I would be helpful of any help / ideas as to what might be going on. (even if I can just identify if it is hardware or software)

thanks

---

