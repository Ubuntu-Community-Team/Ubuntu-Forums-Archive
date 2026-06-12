---
title: "[SOLVED] p2p filesharing?"
date: 2007-08-29
forum: General Help
---

### Post by RuB3N on 2007-08-29
hi,

i switched to ubuntu from vista b/c vista sucks....

but i was woundering if there is and p2p filesharing network type programs use to download mp3's, software, ext. 

is there any programs like that??




thanks for your time:)

---

### Post by Adiuvo on 2007-08-29
I'm going to assume all the things your going to download are freeware...

Anyway, try Deluge. I use it and it fits my needs.

To get it, go to terminal, the type sudo apt-get install deluge.

---

### Post by robotlovee on 2007-08-29
there is frostwire and if u dont want to just download songs you can go to  [www.songbirdnest.com](www.songbirdnest.com) and download songbird.

---

### Post by RuB3N on 2007-08-29
with song bird can you look up any type of music by its name and have a download for it there or is it certin types of music or limited to what you download??

---

### Post by FuturePilot on 2007-08-29
I'm surprised no one mentioned [Frostwire]("http://www.frostwire.com/")

---

### Post by Seti on 2007-08-29
And I'm surprised nobody mentioned [http://http://gtk-gnutella.sourceforge.net/en/?page=news]("http://http://gtk-gnutella.sourceforge.net/en/?page=news"); its the best, IMHO.

---

### Post by por100pre1 on 2007-08-29
amule:

```
sudo apt-get install amule
```

Be sure to share only free (as in freedom) stuff... :wink:

---

### Post by notwen on 2007-08-29
+1 Frostwire, tis' the Linux equivalent of LimeWire. =]

---

### Post by sumguy231 on 2007-08-30
> **notwen said:**
> +1 Frostwire, tis' the Linux equivalent of LimeWire. =]

Not quite, both Frostwire and Limewire have Linux versions. The difference is that Frostwire has a different theme and doesn't nag you to "go pro". And it seems to have a few extra features.

---

### Post by Hallvor on 2007-08-30
> **RuB3N said:**
> hi,

i switched to ubuntu from vista b/c vista sucks....

but i was woundering if there is and p2p filesharing network type programs use to download mp3's, software, ext. 

is there any programs like that??




thanks for your time:)


It depends what you are looking for. In my opinion:
For full albums, software, ebooks or large/rare files in general, aMule.
Large and popular files, tv-series: bittorrent/bittornadu/deluge/ktorrent
Smaller files, single mp3s, etc., limewire/frostwire

---

### Post by RuB3N on 2007-08-30
when i downloaded frostwire i wasnt able to run the program...

im not sure what the problem is??

---

### Post by por100pre1 on 2007-08-30
> **RuB3N said:**
> when i downloaded frostwire i wasnt able to run the program...

im not sure what the problem is??

Try right-clicking it and select to run it with Gdebi.

---

### Post by sumguy231 on 2007-08-30
> when i downloaded frostwire i wasnt able to run the program...
You need to have Java installed. Try installing sun-java5-jre.

---

### Post by RuB3N on 2007-08-31
how do i configure sun-java5

b/c when i install it in the terminal 

a package configuration screen pops up inside the terminal and im not sure what to press to get it to configure

---

### Post by bharani on 2007-09-06
did somebody get amule work on the UBuntu fiesty. no matter how many times i tried it always gives lowid...in India

---

### Post by por100pre1 on 2007-09-06
> **bharani said:**
> did somebody get amule work on the UBuntu fiesty. no matter how many times i tried it always gives lowid...in India

Do you have a router? If so open the following ports in your router:

TCP 4662
UDP 4665
UDP 4672

If you have changed the ports amule uses previously, check in Options> Connection.

If this doesn't help, install Firestarter, a tool for opening ports in your firewall:

```
sudo aptitude install firestarter
```

and open the ports. [Here's]("http://www.fs-security.com/docs/policy-page.php") how to.

Hope this helps. :)

---

### Post by Hallvor on 2007-09-07
> **bharani said:**
> did somebody get amule work on the UBuntu fiesty. no matter how many times i tried it always gives lowid...in India

It could be a case of throttling. Try changing the default ports and see if it helps. There is also a bit of extra information about aMule in my signature.

---

### Post by kesman on 2007-09-07
just use bittorrent or linuxdcplusplus for music and stuff, frostwire just downloads ads on your hdd.

---

### Post by sloggerkhan on 2007-09-07
get deluge from their website. It's my favorite torrent client ever. Very similar to muTorrent/microtorrent. 
[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by Hallvor on 2007-09-07
I don`t think that was what he asked for.

---

### Post by bharani on 2007-09-07
Hello havlor,por.., 
                                         I tried doing whatever is in your signature...basically this is the n/w i have...I donot have a router..All i get from my ISP is an ethernet cable and I get logged in using a client s/w. Now would you please help me regd how to open ports in firestarter..in the inbound policy i add a new rule...what is the service that is to be allowed for Donkey n/w...please help...

Bharani.

---

### Post by bharani on 2007-09-07
anybody

---

### Post by Hallvor on 2007-09-08
You don`t have to install Firestarter. Just copy and paste the lines mentioned there to open default ports. Firestarter is just a GUI frontend to IPtables. It is easier and faster to open the ports using the command line.

Open up the terminal Applications -> Accessories -> Terminal

Copy and paste these lines into the terminal and press enter: 

sudo iptables -A INPUT -p tcp --dport 4711 -j ACCEPT

sudo iptables -A INPUT -p udp --dport 4712 -j ACCEPT


Once you have done this, tcp 4711 and udp port 4712 will be open.

---

### Post by bharani on 2007-09-08
I tried using different ports including the standard one...and issued the command like u said in the previous post...here is my problem...please somebody help me out...

---

### Post by Hallvor on 2007-09-08
Can you post a screenshot of your Preferences ->Connection in aMule?

Read this. Perhaps you`ll find something useful:

[http://www.amule.org/wiki/index.php/FAQ_ed2k#What_is_LowID_and_HighID.3F](http://www.amule.org/wiki/index.php/FAQ_ed2k#What_is_LowID_and_HighID.3F)

You may also get a low ID if your IP-address ends with a zero.

---

### Post by bharani on 2007-09-08
Hello,
              Please look at me screen shots...[COLOR="Red"]"Bearshare"[/COLOR] works in my dual boot system[COLOR="Red"] WinXP[/COLOR]. but the moment i logon to fiesty..It says the port is not open...Also I tried tweaking the port numbers...I hope my ISP in not much a problem...please help.

Bunny.

---

### Post by Hallvor on 2007-09-08
You seem to have done everything correctly. It could be your ISP. But first of all, check if your IP ends with a zero. That will give you a low ID even if the ports are forwarded correctly. If that is the case, all should be fine when you get a new IP from your ISP. [http://whatismyip.com/](http://whatismyip.com/)

If it doesn`t end with a zero, try changing tcp to 1755 and UDP to 443. These are last resort ports, reserved for "important" traffic.

---

### Post by Magneticgravity on 2007-09-08
Deluge is good for  torrents. Azureus is also available but kept closing randomly at times on me.

---

### Post by sloggerkhan on 2007-09-08
> **RuB3N said:**
> with song bird can you look up any type of music by its name and have a download for it there or is it certin types of music or limited to what you download??

Songbird is a way to search the internet for music. It's like an iTunes program that finds music files on the internet which you can add to your library by either downloading them or referencing their web address.

---

### Post by akba0012 on 2007-10-03
> **Hallvor said:**
> Can you post a screenshot of your Preferences ->Connection in aMule?

Read this. Perhaps you`ll find something useful:

[http://www.amule.org/wiki/index.php/FAQ_ed2k#What_is_LowID_and_HighID.3F](http://www.amule.org/wiki/index.php/FAQ_ed2k#What_is_LowID_and_HighID.3F)

You may also get a low ID if your IP-address ends with a zero.

I would actually like to open the gui since i would have no idea what to do after i do the command line. 

I installed the package, tried to open it, but nothing happens after i try to open it from the Applications menu. maybe it has to do with java being installed?

---

### Post by strabes on 2007-10-04
> **akba0012 said:**
> I would actually like to open the gui since i would have no idea what to do after i do the command line. 

I installed the package, tried to open it, but nothing happens after i try to open it from the Applications menu. maybe it has to do with java being installed?

The ubuntu-restricted-extras package will install java.

---

### Post by Kundalinux on 2007-10-09
Amule currently has most of its servers down; a pain in the neck. You can still find some available servers here and input them manually, but there are just a few left so Amule is not what it used to be: [http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html)

I am looking into other p2p solutions. I will give Frostwire a try......

---

### Post by Hallvor on 2007-10-09
> **Kundalinux said:**
> Amule currently has most of its servers down; a pain in the neck. You can still find some available servers here and input them manually, but there are just a few left so Amule is not what it used to be: [http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html)

I am looking into other p2p solutions. I will give Frostwire a try......

That is pure FUD! It is true that many of the large servers went down, but aMule does not need servers for anything else than bootstrapping KAD. And KAD is working as well as ever.

---

