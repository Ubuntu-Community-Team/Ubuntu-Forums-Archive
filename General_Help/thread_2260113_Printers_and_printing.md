---
title: "Printers and printing"
date: 2015-01-09
forum: General Help
---

### Post by mauroj on 2015-01-09
All - I am soliciting help with printing. There are two questions I have.
The first has to do with a specific issue where printing stops working.
The second (potentially easy) is a broad solicitation of "hey all - what
printer do you use on your Ubuntu desktop that is rock solid - has been
working problem free for a long time"? The motivation for the second question
is we're willing to make the investment and buy a new printer if there's
enough feedback on something that works really well.

The current problem is with a Brother printer (3070CW), USB connected
to the Ubuntu desktop. Periodically (every couple months), printing no longer
works - print jobs sit in the queue, the printer is on and ready, but the jobs
never get sent down. Gyrations with System Settings->Printer, etc, do 
not help. The only thing that helps is removing the printer from Ubuntu,
then adding it back. After that, it works again for a while. So it sounds like
a flakey driver that just periodically needs the kick a remove/add sequence generates.

Has anyone had similar experience with Brother printers?
Again, tell me about you "rock solid" printer experience!

FYI - latest Unbuntu release and all updates done.

Thanks
Jim

---

### Post by pdc on 2015-01-10
Jim: I wonder what printer driver you are using with your HL-3070CW?

If you click on this link, [http://localhost:631/printers/](http://localhost:631/printers/) it opens CUPS, printer admin, on your system: look in column 4, Make & Model, and can you copy and paste what is says for your Brother.........and if more than one entry, please tell us

_______________

you could tell us what drivers are installed by copying this command into a terminal ```
dpkg -l | grep Brother 
```     and then copying the result.............and pasting it back here please .......

__________________

My suggestion after all that would be it might ....................be best to delete the current icon for your printer in the PRINTERS section; and then run the install script that Brother provides; and it will do the work of installing printer drivers; and creating an entry for you in lpadmin

if I leave the link for the Brother Install Tool here [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=hl3070cw_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=hl3070cw_all&os=128&dlid=dlf006893_000&flang=4&type3=625) 
______________

I think all the printers from ...........HP, Brother, Canon, Epson work well when they have the correct connections installed ........... it is the connections that can be a bit tricky sometimes..................

This is a usb connection?

---

### Post by Sef on 2015-01-10
> [COLOR=#000000]The second (potentially easy) is a broad solicitation of "hey all - what[/COLOR]
[COLOR=#000000]printer do you use on your Ubuntu desktop that is rock solid - has been[/COLOR]
[COLOR=#000000]working problem free for a long time"?[/COLOR]

I like HP printers; to see what printers are supported, click [here]("http://hplipopensource.com/hplip-web/supported_devices/index.html").

---

### Post by efflandt on 2015-01-10
The best printers for Linux are network printers that support postscript or HP PCL printer languages. *nix has been using postscript for printing since the dawn of time. Then even if you need to swap a printer for some reason it will probably just work, at least temporarily, without even having to change drivers. When our main HP laser printer at our office broke down, which prints both locally and remotely via VPN from our factory order entry computer, I picked up a Lexmark x204n do everything laser for $150US to fill in temporarily. It is the same 1200 dpi and understands HP PCL (and postscript), so all I had to do was assign it the IP address of our main printer and it just worked without changing any drivers (except that it could not duplex, which we would only sometimes do locally). So that got us through until we got a new main HP printer.

I used an HP LaserJet 4L at home for many, many years in Linux. When that finally thought there was a paper jam that wasn't and I was fed up with little used ink jets drying up, I got a Lexmark C543n which is network color laser that does duplex (postscript or HP PCL). At the time Ubuntu did not have a driver for it, so I used the Lexmark C534 driver which simply worked. I later got a C543n for our office, which can subsitute for our main HP printer when it wears out (including duplex). Ubuntu now supports the C543n which Lexmark has discontinued for a newer model.

The point is that if a network printer understands common printing control languages like postscript or HP PCL it should be able to work in Linux even if there is not a specific driver for it. And most network printers or printer servers support HP JetDirect besides lpr/lpd printing protocols even if they do not say so due to trademark.

---

### Post by maco2 on 2015-03-21
Thanks efflandt. Very useful guidance.  Am new to ubuntu. Got 12.04 LTS 64 bit and having serious trouble (due to being a thicko) getting my Canon MP 560 to work. All the convoluted workarounds I have read leave me cold.  Much too complicated for this 80 year old fart. Even got to the point of considering buying a new all-in-one printer that was guaranteed to work out of the box, plug and play.  But finding a current compatible model from HP is another challenge.

Anyong got ideas?    Maco

---

### Post by pfeiffep on 2015-03-21
> **mauroj said:**
> All -  <snip>
Again, tell me about you "rock solid" printer experience!
<snip>
Thanks
Jim
We use an HP phoosmart c6280 which has a network connection. We are able to print wirelessly from a Mac Book Pro (Mac OS), Dell Studio laptop (both Windows and Ubuntu), Dell Inspiron Laptop (Ubuntu) ... th printer is connected via usb to an HP desktop (both Windows and Ubuntu).

---

### Post by pdc on 2015-03-21
so maco2; welcome to the forums; and sorry to hear of your troubles with the MP560

It is a 5year old printer; and back in them days; linux was all 32bit ..........and perhaps surprisingly.............Canon matched that by producing 32bit drivers. 

So Canon make a driver for your printer; that I could guide you to install; but you have leapt ahead and set up a 64bit system; which makes it harder. 

________________

I have seen the workhorse Canon inkjet printers for about US$30 or equivalent in many places: increasingly, replacing the ink cartridges may cost you more .............

..........if you want guidance on the MP560 I can give you that; I see it as 3 steps:

1) set up some symbolic links: to tell the 2010 Canon drivers where to look to find what they need in your 64bit system; (sort of like .............where are my socks dear.........I can't seem to find them.........)
2) install [COLOR="#0000FF"]libtiff4[/COLOR] as ubuntu leaves that out
3) install the Canon drivers 

......details to follow if you ask for them .............

---

### Post by maco2 on 2015-03-22
Thanks pdc for your prompt response. Perhaps I should add that I live in sunny (today) Surrey in the UK.

When I started to look at trying Ubuntu, I chose 12.04 because it was LTS and the 64 bit version because all the pundits seemed to say it was the future.  I never imagined it would cause the problems it has with that most normal of partners, the humble printer!

I only need a fairly basic inkjet printer (print/copy/scan) hence my MP560.  So, if I can get my Ubuntu to work easily and properly with my MP560, that is my obvious first choice.  

I have 2 desk top PC's. One running Win 7 and the second more recent addition running Ubuntu.  My wife has just got a Dell laptop (Win 7 also)  which we hope to link to the printer.

The MP560 is wifi enabled (on) and I have added wireless LAN USB Adaptors 802.11N to the PCs.

I have tried to follow the advice on other posts regarding what is clearly a problem but stumble due to my lack of knowledge. For example,  the screen I have up clearly does not match that used in the answer or I am asked to go somewhere else to I know not where to implement some other task.

If you are willing to treat me with patience, then please, I should be grateful for your help.

Best,  Mac.

---

### Post by pdc on 2015-03-22
thanks Mac; the daffodils should be starting to appear in sunny Surrey? well, let's tackle the 3 steps: 

1) set up some symbolic links:
2) install libtiff4 as ubuntu leaves that out
3) install the Canon drivers

___________

firstly, if we use the terminal to do the work: ............many ways to open it; I suggest holding 3 keys down: control and alt and t and that should open the terminal; ........if for some reason it doesn't work, [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) has other ideas

__________

we need to paste commands into a terminal; whereas in many programmes if one holds down 2 keys: control and v to paste .......... the terminal has a planned difference and it uses 3 keys: shift and control and v ............ or just use your mouse and the top line of terminal; Edit and then down to paste .......

I list the commands you need to paste below inside the code signs: after pasting each line, please hit the ENTER key to make it all happen ........

__________

1) symbolic links 

```
sudo ln -s /usr/lib /usr/lib64
```

```
sudo ln -s /usr/local/lib /usr/local/lib64
```

__________

2) install libtiff4  

if you click on this link [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) it is the very respected Debian repository and if you go 14 down the list, there is an amd64 version of libtiff4 (the first 13 you are see are libtiff-dev which you do NOT want); 

so click on that 14th entry and your system should offer to save or open it .......... in the context of downloading, open should mean *install* and gladly accept the offer of doing that and see it installed ..............

_____________

3) install drivers

having done the groundwork, one now installs the Canon drivers: if you go here, [http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html) and click to download and this time SAVE the package please; that way it ends up in your Downloads folder and the following commands can find it .................. it comes down as cnijfilter-mp560series-3.20-1-i386-deb.tar.gz

......... so in the terminal if still open .....

```
cd Downloads
```

```
tar -zxvf cnijfilter-mp560series-3.20-1-i386-deb.tar.gz
```

```
cd cnijfilter-mp560series-3.20-1-i386-deb
```

```
./install.sh
```

so that last command is the install script: it should ..........do all the work ......... of both installing the drivers AND registering the printer on your system; if it baulks at you having 64bit; and it being 32bit; if you let me know and we can do some direct installing of the drivers; I have subscribed to this thread.............which one does from thread tools top-right........so I can try and keep in touch

good luck!

---

### Post by maco2 on 2015-03-23
'Morning pdc.

Full of enthusiasm on receipt of your reply, I copy it across to my other PC and print it.  On entering at the prompt the first line of the code I get  :- 

[sudo] password for mclean: 


I try to enter my machine password but it refuses to accept any entry at the flashing cursor.  Gggrrrrrrrrrrrrrrrr ! ! !

Now what?

---

### Post by pdc on 2015-03-23
well from what I understand you say; what your computer thinks you told it was the sudo password; and which it holds in its memory; seems to be different from what you typed in a few hours ago; 

__________

if that is so, that is a different ball-game to installing a printer; if I add the title above, some may see this and advise; I can only google on the topic 

here is one suggestion

[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by maco2 on 2015-03-24
Evening pdc.

Yesterday was a bad hair day.  I use a KVM to switch between my 2 PCs and all froze up.  The trouble presented as a BIOS fault on my No.1 computer but my computer man thought it more likely to be the KVM which had been playing up.  My No.2 computer I use exclusively for Ubuntu .

Back in business today, I followed the link you suggested and got as far as selecting   "root   Drop to root shell prompt".  This resulted in the line   "root@ <name> 6150M2MA:~#"  appearing below the panel.  Continuing with the link and believing it necessary to state my existing password for cancellation prior to the creating of the new one, I got the response "password does not exist"  Clearly this is nonsence as I have been using it since new at start up and whenever authentication was required. At this point I baled out as it seemed I was unlikely to get anywhere useful.   I am the only user of this machine.

The person who set up 12.04 for me is really an MS man and did it as a favour.  Is it possible that he misunderstood the meaning of  "Administrator" in MS terms and the much deeper power of it as a root power in Ubuntu? Might this be the cause of the response "password does not exist"?  Or is that just a stupid res herring on my part?

What this has again illustrated is the difficulty I have met so often when I try to follow forum instructions only find it is not replicated on my screen.

I really do not want to give up on this.

Best regards in the hope you can dig me out of this,  Mac.

---

### Post by pdc on 2015-03-24
> The person who set up 12.04 for me is really an MS man and did it as a favour. Is it possible that he misunderstood the meaning of "Administrator" in MS terms and the much deeper power of it as a root power in Ubuntu? 

If he lives close to you in Surrey, best bet might be to go over and knock on his door and ask him: 

............ you do say > Clearly this is nonsence as I have been using it since new at start up and whenever authentication was required. 

............that sort of makes me think you do have a sudo password 

from here [http://superuser.com/questions/553932/how-to-check-if-i-have-sudo-access](http://superuser.com/questions/553932/how-to-check-if-i-have-sudo-access) if you type in a terminal ```
sudo -v
```      .........can you tell us what you get please?

and then try ```
sudo -l
```         and that seems a good way to verify if the system agrees with you Mac

---

### Post by maco2 on 2015-03-25
pdc.

Thanks again.

<me>  = my family name.

As you will see from the following copy, using ctrl + alt + t ,    I typed at the flashing cursor

       sudo -v     and   then    sudo -l    the results you will see below.

 

      <me>@<me>-6150M2MA:~$ sudo -v
       [sudo] password for <me>: 
       <me>@<me>-6150M2MA:~$ sudo -l
      Matching 'Defaults' entries for <me> on this host:
           env_reset,
      secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

     User <me> may run the following commands on this host:
        (ALL : ALL) ALL
     <me>@<me>-6150M2MA:~$ 


Does this make any sense?

Mac.

---

### Post by pdc on 2015-03-25
when I go back over this; the first two commands were to tell the computer to go look for lib in the lib64 directory.................so when you paste in the command ```
sudo ln -s /usr/lib /usr/lib64
``` it will ask you for your sudo password; you type that in and press the enter key; and then you should get a blank terminal; it is waiting for another command; .................meaning ......................it just set up the link we had wanted it to do; in an instant; and like a dog keen to fetch a bone; is sitting waiting and ready ..............do you think that is what you get? If so, move to the next command ```
sudo ln -s /usr/local/lib /usr/local/lib64
```and thence on to the driver install for the 560

---

### Post by maco2 on 2015-03-26
Well pdc,  that was tedious.  I have just succeeded in printing a test page from my Ubuntu machine.  A eureka moment!

I did warn you I needed your patience and understanding and that you certainly provided.

After each of your posts, I hit other snags which sent me scuttling around trying to solve.  This was entirely due to my not understanding at all the way Ubuntu works and what keystrokes I needed to navigate my way through the haze.

At the last, my computer would not allow me to load the drivers due, it turned  out, to there being a problem with the cache for which I was invited to click on "Repair" .  This I did but nothing happened that I could see so I waited, then was called away for over an hour. As I brought back the screen from its slumber,  the Terminal pane appeared and a long list of script scrolled down ending with the magic words " You may now connect you printer "  .  Or words to that effect.

Anyway, a huge thank you for your support from this grateful old fart,  Mac.

---

### Post by pdc on 2015-03-26
well mac; I am delighted for you that your printer now works? .......... we all learn from these things........ good to know that the symbolic links; libtiff4 and then the 386 drivers work well

pleased to be able to help; you will have learnt quite a bit so I actually hope you have more opportunities to tinker with the linux; as it all builds up! best wishes

---

### Post by maco2 on 2015-03-27
Dare I ask you one more thing pdc?

In the midst of all the above, I did an update of the programs already loaded and at the top was an invite to upgrade to 14.04LTS.

Is there any benefit for me in so doing?

Best,  Mac.

---

### Post by speartip on 2015-03-27
maco2.
Remember the old saying. If it ain't broken....
Upgrading goes ok for some, others run into issues. Reinstalling is always preferable to upgrading.
So if your linux knowledge is limited, I would leave well alone.

---

### Post by maco2 on 2015-03-27
Speartip.

I'm quite a believer in that old saying.

Your comments noted and wilco.
Thanks,  Mac

---

