---
title: "Problem with Xine and DVB"
date: 2006-09-13
forum: General Help
---

### Post by zaboron on 2006-09-13
I have a budget DVB card.
I installed & configured all the necessary DVB tools ( i hope)

At least, I have a full channels.conf , i can tune to channels with szap, i can record the stream with dvbstream and watch it.
But i cannot use Xine: when i try to open dvb:// with xine, i get the following error message:

```
xine: found input plugin  : DVB (Digital TV) input plugin
input_dvb: cannot open dvb device
xine: input plugin cannot open MRL [dvb://ASTRA SDT]
xine: cannot find input plugin for MRL [dvb://ASTRA SDT]
xine-lib: error: The xine engine failed to start.: No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

```

what am I doing wrong? I am a linux newbie, so i might have missed something, but i followed the tutorials from linuxtv.org, and searched the web for help, but didnt find anything.

the log from szap:

```
clemens@clemens-desktop:~$ szap RTL
reading channels from file '/home/clemens/.szap/channels.conf'
zapping to 807 'RTL':
sat 0, frequency = 12207 MHz V, symbolrate 27500000, vpid = 0x0000, apid = 0x0000
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
status 01 | signal 86a3 | snr 6db0 | ber 00000003 | unc 00000000 |
status 1f | signal b9da | snr df38 | ber 0000025c | unc 00000000 | FE_HAS_LOCK
[...]

```

dvbtraffic and dvbsnoop seem to be working well, too - at least a lot of numbers are displayed, not that I know if that is a good or bad sign.

---

### Post by MCMcButtah on 2006-09-22
I have this exact same problem with xine. i have tried ubuntu, kubuntu, and mepis with the same result. With mplayer my fusion 3 card works, but only for about a minute or too before getting a too many video packets in buffer message and then it crashes out. What is really frustrating is that I know the card is working as far as the OS is concerned, but I have have spent 2 weeks trying to find a player that can actually play an atsc stream off my capture card. I have tried mplayer, xine, xine-hd, kaffeine, XawTV, kaboodle, vlc, KPlayer, and TVTime. Does anyone have any ideas? Thanks

---

### Post by ThomasMarkas on 2007-04-20
I had the same problem, the following worked for me.

To tune into a channel in one terminal
   tzap -r "BBC TWO"
and leave it running

In another terminal

   xine stdin://mpeg2 < /dev/dvb/adapter0/dvr0
or 
    mplayer - < /dev/dvb/adapter0/dvr0

I am using a Hauppauge NAVO.T.USB2 and it seems fine (on I had the firmware installed).

Annoying that I have not yet found out how to change the channel once set.

---

### Post by gebeleizis on 2007-04-25
> **ThomasMarkas said:**
> I had the same problem, the following worked for me.

To tune into a channel in one terminal
   tzap -r "BBC TWO"
and leave it running

In another terminal

   xine stdin://mpeg2 < /dev/dvb/adapter0/dvr0
or 
    mplayer - < /dev/dvb/adapter0/dvr0

I am using a Hauppauge NAVO.T.USB2 and it seems fine (on I had the firmware installed).

Annoying that I have not yet found out how to change the channel once set.

Thanks for this. It works with my Pinnacle 300i. 
It works, but is a pain pain pain. 
I hope it will be something more precise and easy for common user. 
Long live Ubuntu!

---

### Post by ThomasMarkas on 2007-09-24
gxine has a readme that is installed at the same time and gives instructions on how to configure gxine for DVB. The readme is called README.dvb.gz and was found in /usr/share/doc/libxine1


If you have gxine installed try in a terminal

man /usr/share/doc/libxine1/README.dvb.gz

to view the file .

---

### Post by ThomasMarkas on 2007-09-24
Putting the channels.conf in ~/.xine/channels.conf allow xine to find the channels. This works when starting xine from the menu and picking DVB from the menu bar. Changing channels is a bit slow and sometimes hangs for few moments.

I am using a  Hauppauge NOVA-T-USB2.

---

