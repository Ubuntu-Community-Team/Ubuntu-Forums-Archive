---
title: "Playstation 3 and Linux"
date: 2008-07-09
forum: General Help
---

### Post by Tom--d on 2008-07-09
I need some help with it,

What Distro is the best for the Playstation 3?

Yellow Dog Linux?
Ubuntu?
Anyother, and why?

Can I run the Distro of the LiveCD, Meaning I do not want to partition my Playstation hard drive.

---

### Post by heatblazer on 2008-07-09
I`ve seen ubuntu on PS3 and it was so-so. PS3 is powerful but I don`t know why ubuntu was so strange.

---

### Post by Tom--d on 2008-07-09
> **heatblazer said:**
> I`ve seen ubuntu on PS3 and it was so-so. PS3 is powerful but I don`t know why ubuntu was so strange.

Lack of RAM?

---

### Post by kaola_linux on 2008-07-09
How about knoppix? It is light and has a good hardware compatibility...:)

---

### Post by jay019 on 2008-07-09
Doesnt it need to be a PPC version to run on PS3?

---

### Post by PadreSol on 2008-07-09
YDL has been running the longest on PS3, check it out. Livecd won't work.

---

### Post by Unholy_goat on 2008-07-10
I've tried unbuntu and yellow dog, yellow dog has wireless support but no bluray support, ubuntu has bluray but no wireless support, and the picture isn't that good on either as sony doesn't let linux have full control of the video card i currently use yellow dog on my ps3 but am thinking of switching back to ubuntu as it's more familiar to me

---

### Post by emshains on 2008-07-10
Hell, no! Use ubuntu with a kernel that is optimised for the cell proccessor which is your own ps3's processor. 

Ubuntu should run fine, if its the special ps3 version. You can download it from ubuntu.com. It's installation isnt like your oridinary liveCD, its more (practicly the same) the alternative install of 8.04. 

The ordinary 8.04 live cd is optimised for x86 processors (intel and amd), and since "the cell" is based on a PPC processor and it even then its more different from the ordinary PPC processor, so to use the cell up to its full potencial, or just run normal it has to have a different kernel from the ordinary install. Actually it would run better with the "smp" kernel because it has multiple cores.

Though I have some problems with installing it on my PS3, because the installer cant recognise the partitions I made with PS3-os (called PSX), but I have seen many people who have installed it and it runs like a dream.

---

### Post by emshains on 2008-07-10
> **Unholy_goat said:**
> I've tried unbuntu and yellow dog, yellow dog has wireless support but no bluray support, ubuntu has bluray but no wireless support, and the picture isn't that good on either as sony doesn't let linux have full control of the video card i currently use yellow dog on my ps3 but am thinking of switching back to ubuntu as it's more familiar to me

It has wi-fi support with the PS3 install of ubuntu!

---

### Post by emshains on 2008-07-10
> **kaola_linux said:**
> How about knoppix? It is light and has a good hardware compatibility...:)

Actually it hasnt got such a good hardware compability, because it is actually meant to be a live distro, it isnt made for regular use. I use it to repair my system when it wont boot. Gentoo would be better because it can be light.

---

### Post by Tom--d on 2008-07-10
Thank you for your help.

I installed Ubuntu 7.10 PS3 version. 
Installed fine.
Booted up. All went fine. Desktop and everything.
Im able to change the res through the terminal,
ps3videomode
Got it to 1080i at 50hz,
But it was not 50hz, it was 30hz and it was crappy. Quality was poor. 720p didnt have this. I tried the 60hz option and still getting 30hz.
And yes, My tv supports up to 1080i. I know as the ps3 os is in 1080i

I tried Yellow Dog Linux.
Got wireless working :)
And again, I prefer Ubuntu due to im used to it. 
And the same problem with YDL with the res. Low refresh rate :(

Also, It only uses 2 cores of the 6 there? (is this true)
Lack of ram you can tell.

I thought Sony would do a better job of it. Maybe an addon to the RAM would be good. I know you can use your memory stick for Swap.

Anyother ideas?

---

### Post by Tom--d on 2008-07-11
No one?

---

### Post by manbish on 2008-07-11
> **emshains said:**
> It has wi-fi support with the PS3 install of ubuntu!

PS3 has wifi support.  I have a Belkin G USB network adapter F5D7050 V4000 with driver zd1211rw driver.  I am running xubuntu 7.10.  My PS3 is at 2.36.  I tried virtually all the ubuntu and xubuntu ps3 options and xubuntu 7.10 came closest to working with the netwrok adapter, before I edited system using terminal.

I then opened terminal and typed:

sudo nano /etc/dhcp3/dhclient.conf

In the resultant config file that you can now see, just before the request line, alter the prepend line by removing the # sign and ensure the line reads:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Use the cursor keys to move up and down in the file.  When you have finished editing, use the ctrl key together with x to exit the file and type

y

for 'yes' at the prompt, followed by the return key at the next prompt.

(You now need to edit your router using your pc to alter the DNS to read:

208.67.222.222
208.67.220.220

These are opendns numbers, and the opendns website gives help on atering the router if you need it).

Continuing in the terminal screen type the following lines using the return key between each line.  Items in <> are items you need to name yourself, omitting the <> symbols:

lshw -C network

This will return items including your network adapter, ie eth1, wlan1, rausb0

sudo ifconfig <eth1, rausb0, wlan1, as specified by your ssytem> down
sudo dhclient -r <eth1>
sudo ifconfig <eth1> up
sudo iwconfig <eth1> essid "<broadcast name of your network>"
sudo iwconfig <eth1> mode Managed
sudo dhclient <eth1>

If it has worked, you will have a network connection.  The network manager will show no connection, but ignore this.

You will need to review the Ubuntu pages to find out how to install the firefox plugins that allow it to use java, flash, pdf, realplayer, etc.  I have not done this for a powerpc system before, so I am not sure what success you will have for that.

The networking troubleshooter is at:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28ipv6%29#ifconfig](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28ipv6%29#ifconfig)

Credit for the above advice all goes to the writers of the troble shooting guide.

---

