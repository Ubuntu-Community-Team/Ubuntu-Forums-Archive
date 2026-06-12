---
title: "Ares via giFT"
date: 2008-07-02
forum: General Help
---

### Post by rapper97 on 2008-07-02
Despite reading a [past thread]("http://ubuntuforums.org/showthread.php?t=198945") indicating that giFT is moribund, it looks like [KCeasy]("http://www.kceasy.com/")'s still being supported and there's [an updated plugin for Ares]("http://gift-ares.berlios.de/"). So someone must have gotten Ares to work on Linux... right?

I was initially having problems connecting to any networks using Apollon , giFToxic or giFTui but after updating Gnutella's node file, I was able to connect fine. However, I haven't had the same luck after updating Ares' nodes.

Running [FONT="Monospace"]giftd -v[/FONT] from the command line, I get the following output:
```
[20:07:42] giftd 0.11.8.1 (May 14 2007 16:14:22) started
[20:07:42] Plugin Ares (0.3.0) successfully loaded and initialized
[20:07:42] Ares: asp_plugin.c:230(asp_giftcb_start): Starting up.
[20:07:42] Ares: as_ares.c:88(as_init): Initializing Ares library...
[20:07:42] Ares: as_node_man.c:492(as_nodeman_load): Loaded 400 nodes from node file
[20:07:42] Ares: as_session_man.c:97(as_sessman_connect): Requested: 4, connected: 0, connecting: 0
[20:07:42] Plugin Gnutella (0.0.10.1) successfully loaded and initialized
```
 
Then it loads the shared files and all the activity shown is Gnutella-related... until you Ctrl-C, at which point you get
 
```
[20:07:42] Ares: asp_plugin.c:284(asp_giftcb_destroy): Shutting down.
[20:07:42] Ares: as_node_man.c:538(as_nodeman_save): Saved 400 nodes in node file
[20:07:42] Ares: as_ares.c:226(as_cleanup): Cleaning up Ares library...
[20:07:42] Ares: as_session_man.c:97(as_sessman_connect): Requested: 0, connected: 0, connecting: 10
```

So clearly *something* is happening/going wrong with the Ares plugin, I just don't know what it is, exactly (invalid nodes?) or how to fix it.



**UPDATE:**
So, after looking over my post a little bit, I decided to try upping the number of supernodes to connect to from the setup default (not wanting to [overdo]("http://ubuntuforums.org/showthread.php?p=5279672") it!) and that let Ares grab a valid one and connect fine.

---

### Post by Skerit on 2008-08-03
Does anyone have working node files for ares or fasttrack or openft? Only Gnutella is working, but there are no decent search results on that.

I heard gift is kinda dead. I saw on the homepages of apollon & giftui that the last updates were from 2005... A shame :(

---

### Post by test3 (on suse) on 2009-02-20
> **Skerit said:**
> Does anyone have working node files for ares or fasttrack or openft? Only Gnutella is working, but there are no decent search results on that.

I heard gift is kinda dead. I saw on the homepages of apollon & giftui that the last updates were from 2005... A shame :(

[http://rs520.rapidshare.com/files/199837047/gift.rar]("http://rs520.rapidshare.com/files/199837047/gift.rar")  > ares and openFT (and gnut) (and.. may be fasttrack...???)    updated nodes  (works today)

---

### Post by francesco.spegni on 2009-07-05
> **test3 (on suse) said:**
> [http://rs520.rapidshare.com/files/199837047/gift.rar]("http://rs520.rapidshare.com/files/199837047/gift.rar")  > ares and openFT (and gnut) (and.. may be fasttrack...???)    updated nodes  (works today)

hi, 

i'm facing the same problem, i've recently discovered the giftd project but after configuring it and forwarding the router ports, it seems it is not able to connect to any node from the nodes file.

does any of you actually use giftd + openft + gnutella + fasttrack + ares ? and which nodes file list do you actually use?

furthermore, i tried to compile gift-ares-0.3.0 sources with giftd-0.11.8.1 taken from the ubuntu repositories and i got the following error:

as_ares.h:57:36: error: libgift/proto/protocol.h: No such file or directory

i've seen i've a /usr/include/libgift directory, but i've not a proto/protocol.h file over there. does it compile only with previous versions of giftd?

thanks for anyone that could help.

PS
i tried to access the above gift.rar linked file, but rapid share tells me that the file does not exist anymore... could someone upload it again, please?

---

### Post by Soul-Sing on 2009-07-05
Didn't [COLOR="Red"]apollon[/COLOR] came with "/main/plugins":
OpenFT:Gnutella:FastTrack:Ares? via gift setup?

cd /tmp
wget [ftp://ftp.berlios.de/pub/gift-fasttrack/dists/unstable/main/binary-i386/libfasttrack-gift_0.8.9-1_i386.deb](ftp://ftp.berlios.de/pub/gift-fasttrack/dists/unstable/main/binary-i386/libfasttrack-gift_0.8.9-1_i386.deb)
wget [http://d250931.u35.fr.digiweb.ie/fichiers/libares-gift_0.2.2-0.1_i386.deb](http://d250931.u35.fr.digiweb.ie/fichiers/libares-gift_0.2.2-0.1_i386.deb)
sudo dpkg -i libfasttrack-gift*.deb libares-gift*.deb

```
sudo gift-setup
```

/main/plugins: OpenFT:Gnutella:FastTrack:Ares
enter by default.

---

### Post by francesco.spegni on 2009-07-05
i think the link you posted are not working (at list the libares one).

btw i found the reason why i was not able to compile gift-ares: i didn't install the libgiftproto-dev. i solved doing

sudo apt-get install libgiftproto-dev

and then compiling the gift-ares source files (./configure -> make -> checkinstall -> dpkg -i <deb_file>).

now i've entered OpenFT:Gnutella:Ares as /main/plugin and i've executed giftd -d (daemon). all seems working fine. i've also launched giftui and it seems i'm not able to connect to any node (see the attached screenshot). i even left giftd/giftui running for several minutes, hoping that it would finally find any peer to connect, but anything changed after one hour waiting...

is there a way to check whether i'm connected to other nodes or not? maybe i should look for some particular strings appearing in the ~/.giFT/giftd.log file?

thanks in advance for your help

---

