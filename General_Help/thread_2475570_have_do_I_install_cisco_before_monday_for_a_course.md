---
title: "have do I install cisco before monday for a course?"
date: 2022-06-01
forum: General Help
---

### Post by smallville1979 on 2022-06-01
[https://skillsforall.com/launch?id=9762b32d-0a49-4d7a-b881-498eb3be42cc](https://skillsforall.com/launch?id=9762b32d-0a49-4d7a-b881-498eb3be42cc)
[FONT=sans-serif]Ubuntu (Linux)[/FONT]
[FONT=sans-serif]Packet Tracer can be installed via CLI[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]using user credentials with elevated privileges[/FONT][FONT=sans-serif].[/FONT]
[FONT=sans-serif]a.[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Open a terminal and n[/FONT][FONT=sans-serif]avigate to the[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]location where you saved the Packet Tracer installation file.[/FONT]
[FONT=sans-serif]b.[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Enter the following command to install[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Packet Tracer[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]and provide the[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]user password[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]when prompted.[/FONT]
[FONT=monospace]User@[/FONT][FONT=monospace]U[/FONT][FONT=monospace]buntu[/FONT][FONT=monospace]:~/Downloads$[/FONT][FONT=monospace] [/FONT][FONT=monospace]sudo apt[/FONT][FONT=monospace]-[/FONT][FONT=monospace]get[/FONT][FONT=monospace] [/FONT][FONT=monospace]install ./[/FONT][FONT=monospace]Cisco[/FONT][FONT=monospace]PacketTracer[/FONT][FONT=monospace]_xxx[/FONT][FONT=monospace]_Ubuntu_64bit[/FONT][FONT=monospace].deb[/FONT]
[FONT=sans-serif]where xxx[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]is Packet Tracer version.[/FONT]
[FONT=sans-serif]c.[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]The[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Setup[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]dialog opens to the[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]License Agreement[/FONT][FONT=sans-serif]. Read through the agreement[/FONT][FONT=sans-serif]. Use the tab key to[/FONT]
[FONT=sans-serif]highlight[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]<OK>[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]and press[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Enter[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]to continue.[/FONT]
[FONT=sans-serif]Note:[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]The mouse does not work while installing Packed Tracer using CLI.[/FONT]
[FONT=sans-serif]d.[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Use[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]the[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]tab[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]key[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]to select[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]<Yes>[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]and press[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]Enter[/FONT][FONT=sans-serif] [/FONT][FONT=sans-serif]to accept the License Agreement

computer name tom@tom-OptiPlex-3080:~$ 

I am hopeless at command line processing and not sure what I change? 
downloaded the deb it wont run on application installer. I need to know my command line code please before monday morning. unbuntu 22.04. 

[/FONT]

---

### Post by TheFu on 2022-06-01
details matter.

This is incorrect for a few reasons.
```
sudo apt-getinstall ./CiscoPacketTracer_xxx_Ubuntu_64bit.deb
            ^--- space missing here.
     ^^^^^^^----  apt-get cannot install .deb files. Other tools can.

```
Try this:
```
sudo     **apt**    install      ./CiscoPacketTracer_xxx_Ubuntu_64bit.deb

```It assumes the .deb file is in the same directory the shell is in currently.

BTW, posting stuff from a terminal here should be really easy. How?

Select the text in the terminal (yes, selecting it should be enough) - all the relevant lines at once, 
paste it into the browser, then 
inside the textentry area in the browser, select the text and press the "#" button of the advanced editor (Adv Reply).  
That will wrap it in the code-tags.  All the columns will be aligned. It will look on the webpage here like it does in the terminal (without colors, thankfully!).  This method prevents the typo that was somehow added above.

If you aren't using the Adv Reply method you can wrap the text with bold, italics, quotes .... then change the tag "B" ---> "code" at the start and end of the area.  "B", "I", "QUOTE" can each be replaced by "code" in both places and that is sufficient.  The tags are NOT case sensitive.

---

### Post by coffeecat on 2022-06-01
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by ActionParsnip on 2022-06-01
You can install the deb using the commands by TheFu. You may fail deps (I've not installed a deb in ages) but you can resolve deps with:
```

sudo apt -f install

```
Assuming you have the deps available (Should do). Your link doesn't work by the way. It requires a login to view

---

### Post by TheFu on 2022-06-01
**apt** looks at the dependencies inside the .deb file and will install those too, unlike the dpkg tool.

---

