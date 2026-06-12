---
title: "Intel Pro Wireless 2200B/G. Alive but not kicking!"
date: 2005-10-15
forum: General Help
---

### Post by frobroj on 2005-10-15
Hello all I am really new to Ubuntu and I love it so far!!! I have a Sabio Digital Whitebook with Breezy installed. 
However I need some help with my wireless. Breezy installed the adaper during install and Identifies it correctly as a Intel Pro Wireless 2200B/G. I can set the SSID and the Wep Key but it doesnt pull dhcp and it doesnt seem to activate. When activating it takes a while and then says active but it doesnt pull an address and cant get anywhere. Does anyone have any tips for testing general connectivity? I have tried hard setting it and still cant ping the gateway. Just wondering what I might be looking for in the config and on the machine that might indicate the adapter is functioning. Note Its only worked with with Linspire which I am assuming uses NDIS Wrappers. 
Any tips or trick to test the device would be greatly appreciated.

Thanks All!
Fro

---

### Post by matthew on 2005-10-15
I am about to crash so this will be short, but I wanted to give you something to start with.

Begin by disabling (temporarily) the WEP on your router if you can. Test the unencrypted connection and see if you are able to use the internet that way.

If that works, then start over with WEP. Re-enter your keys.

I am using WPA and set up my computer with Breezy first by confirming the unencrypted connection worked, then WEP, and then going to full WPA as is my habit. If the router belongs to you I suggest doing the same...I noticed you already posted on luca_linux's ipw2200 and wpa thread. He is the intel wireless guru around here.

---

### Post by frobroj on 2005-10-15
Well I will give that a try tomorrow. I dual boot the machine and it works with the wep on my windows partition. Thanks for the reply. I will peek around to see if there is any more info on wireless commands like iwconfig and iwlist and what kind of info I can gather from them... When I get to the bottom of it I will post what I learn. There should be a way to see all broadcasted SSIDs. One would think.. Well I will see what I can find. Thanks again....

---

### Post by net_benjo on 2005-10-16
Hi,

I've just installed Breezy on my HP dv4170ca laptop.  I have the exact same problem  as described above.  Ubuntu recognizes my wireless network card, but nothing happens when I activate it....any help with this with this would be great...

this is output of my iwconfig:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:"bosna"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

sit0      no wireless extensions.

thanks

ben

---

### Post by Adamal on 2005-10-16
I have the Intel Pro Wireless 2200B/G card for my laptop but it's working.  The only issue that I've had with Breezy is that when I'm downloading files the wireless dies every once in a while for about a second or two but then auto-reconnects.

---

### Post by xMetaRidley on 2005-10-16
[QUOTE=Adamal]I have the Intel Pro Wireless 2200B/G card for my laptop but it's working.  The only issue that I've had with Breezy is that when I'm downloading files the wireless dies every once in a while for about a second or two but then auto-reconnects.[/QUOTE]

Try [this]("http://ubuntuforums.org/showthread.php?p=409921#post409921").

---

### Post by dailer on 2005-10-16
[QUOTE=net_benjo]
eth0     **radio off**  ESSID:"bosna"
[/QUOTE]

Your wireless card is not activated. You have to activate it somehow.

---

### Post by kake on 2005-10-16
As the previous poster noted, you will have to activate your radio if it says it's off. Some notebooks have a exterior button that activates it, which i do.

Also, check [http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php) for any updated dsdt for your notebook. It fixes alot of problems with ACPI for some of the newer notebooks, or just old and ignored.

I had to use a custom dsdt with ipw2200 even though my ubuntu install said everything was ok.

On my travelmate 8104 i had to a add a line to get the exterior led button to work. look for something equal for your machine if the exterior button doesn't work for you. Only tested this with travelmate 8104 using ipw2200 drivers though. For different drivers and notebook there will have to be made some changes.

/etc/modprobe.d/ipw2200

Should contain:

options ipw2200 led=1

---

### Post by frobroj on 2005-10-16
Wow great info!!
Kake thanks that worked to get the LED and button functioning! And a big thanks to everyone else for all the great responses!
I think the first post from matthew may be correct about disabling my wep. The 128 bit 26 character key works great in windows but in linux I am getting nothing but "invalid crypt:177" in my iwconfig.
Thanks again all

---

### Post by frobroj on 2005-10-16
Wow What a newbie I am... Matthew was correct! it was the wep. I didnt realize that I had to change the linux wep key type to hexidecimal... Works great now! 
Thanks everyone!!!!

---

### Post by matthew on 2005-10-16
[quote=frobroj]Wow What a newbie I am... Matthew was correct! it was the wep. I didnt realize that I had to change the linux wep key type to hexidecimal... Works great now! 
Thanks everyone!!!![/quote]
Congratulations! Enjoy the feeling of exhileration after solving a difficult problem.

---

