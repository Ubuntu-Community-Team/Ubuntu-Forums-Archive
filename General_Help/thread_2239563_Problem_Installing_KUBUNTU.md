---
title: "Problem Installing KUBUNTU"
date: 2014-08-14
forum: General Help
---

### Post by anon_private on 2014-08-14
Hi,

I have a problem after installing KUBUNTU 12.04.4 from a live DVD-R.

The dvd works well and I checked the disk and memory before installing - both fine.

I installed using the icon within the live DVD.

All seemed to go well. I assume that kubuntu has replaced the faulty Vista - not dual boot.

It took quite some time at 97%, but I got the message that kubuntu had been successfully installed.

After re-booting, I got many vertical black and white lines, at the booting stage.

The screen then appeared.

The mouse and keyboard do not work properly. For example, in the search box the cursor is fixed.

The panel where the install icon was has no tool.

It is almost as if things have not loaded properly.

I re-booted a couple of times, but the problems remain.

Advice please

PS. I am now using the live DVD.

____________________________________________

More information:


Using Dolphin:


Home, Network, and Root were made today.


I have two disk entries.


231.8 GiB (my actual disk size is 250GB) - made today


660.8 MiG (looks like the dvd-r disk) modified Feb, 04. I don't understand this date, I bought the disk last week


Can someone explain the disks.

---

### Post by oldos2er on 2014-08-14
What are the hardware specs, particularly graphics card?

---

### Post by anon_private on 2014-08-14
Video Card Nvidia Geforce 7300 Turbocache 256 MB DVI/VGA output with 1xS-Video Output.

Note I can run the liveDVD without a problem.

Some components may need updating - they were not all updated.

Should I re-install

---

### Post by SeijiSensei on 2014-08-14
Is there a reason you're not installing Kubuntu 14.04?  It is the current long-term release.

The date on the DVD is probably the date of the software on it.  

If you're having graphics problems during installation, try pressing F6 at the initial text menu and choose "nomodeset".  Older NVIDIA cards like yours often need this.

---

### Post by anon_private on 2014-08-15
> **SeijiSensei said:**
> Is there a reason you're not installing Kubuntu 14.04?  It is the current long-term release.

The date on the DVD is probably the date of the software on it.  

If you're having graphics problems during installation, try pressing F6 at the initial text menu and choose "nomodeset".  Older NVIDIA cards like yours often need this.

I have just re-installed Kubuntu 12.04.4 and things seem to be working well. I might have re-started a little too early last time (guess).

I decided to install ver 12 because I believe that it uses less RAM than ver 12. I only have 1 GB RAM, but now I have a 1GB Swap partition as well.

Why am I using some swap space, when there is still plenty of RAM to be used?

Thank you

Ps Just installed Firefox, a more advanced browser.

---

### Post by mörgæs on 2014-08-15
I don't know about Kubuntu but in the Ubuntu series 14.04 is less demanding than 12.04. If in doubt I would always go for the latest.

---

### Post by anon_private on 2014-08-15
On re-booting this morning I am having a problem

The KDE wallet kept appearing preventing me from logging in.

I eventually agreed to give it complete access.

On trying to login I could not gain access.

I have now accidently closed the network centre, so that I cannot gain internet access.

How can I get the centre back on the bottom panel.

I was wondering if I need to set anything up

I don't know what DHCP ID is.

Thanks

---

### Post by J_Me on 2014-08-15
dhcp = dynamic host configuration protocol, your isp should have told you if your using a static or dhcp connection.
If connecting to your router via wifi the wifi password will be stored in your wallet so activate your wallet before trying to connect to the internet, if your using a rj45 cable just plug it in no wallet needed to connect.

To get your internet/volume/clipborad widgets back
-right click on a panel
-select panel options
-unlock widgets(if you need to)
-select add widgets
-search for 'system tray' drag and drop onto your panel
-lock widgets after your done
> I decided to install ver 12 because I believe that it uses less RAM than ver 12. I only have 1 GB RAM, but now I have a 1GB Swap partition as well.I have both kubuntu 12.04 and 14.04 on a system with 1gb of ram and don't see much difference.

---

### Post by anon_private on 2014-08-15
> **J_Me said:**
> dhcp = dynamic host configuration protocol, your isp should have told you if your using a static or dhcp connection.
If connecting to your router via wifi the wifi password will be stored in your wallet so activate your wallet before trying to connect to the internet, if your using a rj45 cable just plug it in no wallet needed to connect.

To get your internet/volume/clipborad widgets back
-right click on a panel
-select panel options
-unlock widgets(if you need to)
-select add widgets
-search for 'system tray' drag and drop onto your panel
-lock widgets after your done
I have both kubuntu 12.04 and 14.04 on a system with 1gb of ram and don't see much difference.

Thank you for responding.

I connect using wi-fi, no cable.

I think I am using a dynamic IP (do I need any info, if so, where can I obtain it. I can login using live dvd's, pendrives)

Do I have to use this wallet to connect - This is a new concept (to me).

What does unlocking widgets mean/do.

It would be better for me to use 14.04 and if you can use it with 1GB of RAM, then I should be able to as well.

When I could connect, I noticed that there was a button for me to upgrade.

If I used this button would any files or changes that I have input into ver 12 be erased or reset.

Would I need to start at the beginning.


Thanks

PS. I'll try your suggestions when I next try to use Kubuntu

---

### Post by SeijiSensei on 2014-08-15
I'd install 14.04 from scratch.  It doesn't sound like you've been using the machine enough to have a lot of customizations to preserve.

Usually I create a separate partition for /home when installing in case I want to change the OS and preserve my files.

The wallet contains encrypted versions of passwords like the one for your router.  I found it more intrusive in 12.04 than it seems to be in 14.04.  Also you can disable the wallet entirely from System Settings.

I'd add another gigabyte of memory if you can.  It would be the most effective upgrade for your system, followed by a newer NVIDIA card if you want to watch videos.  

As for RAM and swap, Linux has a very efficient memory manager.  You'll often see swap in use and some physical memory unused.  Most unused memory is devoted to caching disk transactions.

---

### Post by anon_private on 2014-08-15
> **SeijiSensei said:**
> I'd install 14.04 from scratch.  It doesn't sound like you've been using the machine enough to have a lot of customizations to preserve.

Usually I create a separate partition for /home when installing in case I want to change the OS and preserve my files.

The wallet contains encrypted versions of passwords like the one for your router.  I found it more intrusive in 12.04 than it seems to be in 14.04.  Also you can disable the wallet entirely from System Settings.

I'd add another gigabyte of memory if you can.  It would be the most effective upgrade for your system, followed by a newer NVIDIA card if you want to watch videos.  

As for RAM and swap, Linux has a very efficient memory manager.  You'll often see swap in use and some physical memory unused.  Most unused memory is devoted to caching disk transactions.

If I decided to upgrade I would use the upgrade button - via Muon. Out of interest, would I lose information?

Have you found much difference between 12 and 14 in terms of memory requirement?

After getting my connection back, I typed in the router key and the wallet appeared, I then typed the wallet passowrd in and was connected. I note the wallet can be disabled, but I'll keep it for the time being. Can I view its contents?

I don't plan to upgrade my hardware, I don't need to.

I can't see flash in Muon?

'[COLOR=#C61919][B]Hello anon_private,The next UOS will take place between the 12th and 14th November. More details to follow  [here]("http://summit.ubuntu.com/uos-1411/")'

The next what?
[/B][/COLOR]

Just upgraded to ver 14.

So far, so good.

Glad to see the grey has been replaced.

I have kept the dvd-r for ver 12, so I could return to the earlier package. Hopefully, this will be unnecessary.

Is it posible to change the colour of the application icons that appear in the bottom panel when the pages are minimised. In addition, Can the lettering on these icons be ehhanced.

Thanks

---

### Post by SeijiSensei on 2014-08-16
Try switching to the Oxygen theme with System Settings > Workplace Appearance > Desktop Theme.

You can change the fonts used in various desktop objects with System Settings > Application Appearance > Fonts.

KDE lets you customize just about every object.  Browse through System Settings to see what's available.

---

### Post by anon_private on 2014-08-17
Thank you

---

