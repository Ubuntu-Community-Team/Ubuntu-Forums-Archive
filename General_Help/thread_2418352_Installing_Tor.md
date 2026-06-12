---
title: "Installing Tor"
date: 2019-05-05
forum: General Help
---

### Post by moto1860 on 2019-05-05
I'm trying to install tor following the instructions on their website, I've downloaded my 64-bit file which is now in my downloads folder.

[COLOR=#1A1A1A][FONT=Helvetica]Download the architecture-appropriate file above, save it somewhere, then run one of the following two commands to extract the package archive:
[/FONT][/COLOR][COLOR=#1A1A1A][FONT=Inconsolata]tar -xvJf tor-browser-linux64-8.0.8_[/FONT][/COLOR]LANG[COLOR=#1A1A1A][FONT=Inconsolata].tar.xz


[/FONT][/COLOR]```
xxxxx-non-vPro:~$ tar -xvJf tor-browser-linux64-8.0.8_LANG.tar.xztar (child): tor-browser-linux64-8.0.8_LANG.tar.xz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
xxxxx-non-vPro:~$ 



```[COLOR=#1A1A1A][FONT=Inconsolata]


How do I go on about it? Thanks[/FONT][/COLOR]

---

### Post by NM5TF on 2019-05-05
I guess we shall assume that you were in your Downloads folder when you ran the above command ???

like this....

```
[tommy@tommy ~]$ cd Downloads
[tommy@tommy Downloads]$ 

```

---

### Post by moto1860 on 2019-05-05
```
avo@avo-Latitude-E5430-non-vPro:~$ cd Downloadsavo@avo-Latitude-E5430-non-vPro:~/Downloads$ tar -xvJf tor-browser-linux64-8.0.8_LANG.tar.xz
tar (child): tor-browser-linux64-8.0.8_LANG.tar.xz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
avo@avo-Latitude-E5430-non-vPro:~/Downloads$ 



```

---

### Post by deadflowr on 2019-05-05
I'm not sure there is any such version for LANG.
That should be replaced with your Language version.

But the easiest way to get it right is to input the first few characters of the filename and then hit the TAB key.
That will autofill the correct filename.

---

### Post by NM5TF on 2019-05-05
@moto1860

while in your Downloads folder type

```
ls
```

that will list all files in the folder.....look for the tor-browser file...I suspect that deadflower is correct as usual and the LANG portion of the file
name will be something other than just LANG.....maybe something like [COLOR="#FF0000"]tor-browser-linux64-8.0.8_ENG.tar.xz[/COLOR]  if your preferred language is English

type 

```
tar -xvjf 
```

then just copy/paste the correct file name into the command & run it

---

### Post by Rubi1200 on 2019-05-06
If you are on 18.04 then I do not understand why you are trying to do it like this when Tor is available in the repositories:
[https://packages.ubuntu.com/bionic/tor](https://packages.ubuntu.com/bionic/tor)

Install Synaptic Package Manager, search for Tor, mark for installation and then search in applications and run, could not be easier.

And another thing, just some friendly advice: first search the package list for your version before running around on the internet trying to download and install from tar. You will save yourself a lot of work and headaches.

---

### Post by moto1860 on 2019-05-07
> **Rubi1200 said:**
> If you are on 18.04 then I do not understand why you are trying to do it like this when Tor is available in the repositories:
[https://packages.ubuntu.com/bionic/tor](https://packages.ubuntu.com/bionic/tor)

Install Synaptic Package Manager, search for Tor, mark for installation and then search in applications and run, could not be easier.

And another thing, just some friendly advice: first search the package list for your version before running around on the internet trying to download and install from tar. You will save yourself a lot of work and headaches.
I don't know what goes wrong but when I search for it in the applications it doesn't show....
It shows among installed under Ubuntu Software. From there I hit 'launch', nothing happens.

---

### Post by Rubi1200 on 2019-05-08
If you open a terminal and start it ```
tor
```

what error messages, if any, do you get?

---

### Post by moto1860 on 2019-05-08
```
avo@avo-Latitude-E5430-non-vPro:~$ torMay 09 04:23:20.131 [notice] Tor 0.3.2.10 (git-0edaa32732ec8930) running on Linux with Libevent 2.1.8-stable, OpenSSL 1.1.0g, Zlib 1.2.11, Liblzma 5.2.2, and Libzstd 1.3.3.
May 09 04:23:20.131 [notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
May 09 04:23:20.138 [notice] Read configuration file "/etc/tor/torrc".
May 09 04:23:20.141 [notice] Scheduler type KIST has been enabled.
May 09 04:23:20.141 [notice] Opening Socks listener on 127.0.0.1:9050
May 09 04:23:20.141 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 09 04:23:20.141 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 09 04:23:20.141 [err] Reading config failed--see warnings above.
avo@avo-Latitude-E5430-non-vPro:~$ 



```

sorry for the late replies guys, doing night shifts at work.

---

### Post by moto1860 on 2019-05-11
Any ideas?

---

### Post by Rubi1200 on 2019-05-11
Not really, sorry.

Only thing I can think of is that somehow things got messed up between the manual install you were trying and the install from the repos.

I would manually remove the tar and other files you downloaded and then purge the package before attempting a reinstall.

```
sudo apt purge tor
```

```
sudo apt update
```

```
sudo apt install tor
```

---

### Post by monkeybrain20122 on 2019-05-12
Just right click the tarball you downloaded and choose 'extract here". The tar command basically just for extracting the archive.

---

### Post by moto1860 on 2019-05-13
Thanks for the patience, unfortunately I'm having the same outcome: 
```
avo@avo-Latitude-E5430-non-vPro:~$ torMay 14 02:49:16.620 [notice] Tor 0.3.2.10 (git-0edaa32732ec8930) running on Linux with Libevent 2.1.8-stable, OpenSSL 1.1.0g, Zlib 1.2.11, Liblzma 5.2.2, and Libzstd 1.3.3.
May 14 02:49:16.620 [notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
May 14 02:49:16.620 [notice] Read configuration file "/etc/tor/torrc".
May 14 02:49:16.623 [notice] Scheduler type KIST has been enabled.
May 14 02:49:16.623 [notice] Opening Socks listener on 127.0.0.1:9050
May 14 02:49:16.623 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 14 02:49:16.623 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 14 02:49:16.623 [err] Reading config failed--see warnings above.
avo@avo-Latitude-E5430-non-vPro:~$ 



```

@monkeybrain
I had already done that (of course I've now removed both the tar and the extracted file trying to follow Rubi's suggestion.

So following [this]("https://askubuntu.com/questions/833021/could-not-bind-to-127-0-0-19050-address-already-in-use-is-tor-already-running") I got this:

```
avo@avo-Latitude-E5430-non-vPro:~$ torMay 14 20:24:38.915 [notice] Tor 0.3.2.10 (git-0edaa32732ec8930) running on Linux with Libevent 2.1.8-stable, OpenSSL 1.1.0g, Zlib 1.2.11, Liblzma 5.2.2, and Libzstd 1.3.3.
May 14 20:24:38.915 [notice] Tor can't help you if you use it wrong! Learn how to be safe at https://www.torproject.org/download/download#warning
May 14 20:24:38.915 [notice] Read configuration file "/etc/tor/torrc".
May 14 20:24:38.917 [notice] Scheduler type KIST has been enabled.
May 14 20:24:38.917 [notice] Opening Socks listener on 127.0.0.1:9050
May 14 20:24:38.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
May 14 20:24:39.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
May 14 20:24:39.000 [notice] Bootstrapped 0%: Starting
May 14 20:24:39.000 [notice] Starting with guard context "default"
May 14 20:24:40.000 [notice] Bootstrapped 5%: Connecting to directory server
May 14 20:24:40.000 [notice] Bootstrapped 10%: Finishing handshake with directory server
May 14 20:24:40.000 [notice] Bootstrapped 15%: Establishing an encrypted directory connection
May 14 20:24:40.000 [notice] Bootstrapped 20%: Asking for networkstatus consensus
May 14 20:24:40.000 [notice] Bootstrapped 25%: Loading networkstatus consensus
May 14 20:24:44.000 [notice] I learned some more directory information, but not enough to build a circuit: We have no usable consensus.
May 14 20:24:44.000 [notice] Bootstrapped 40%: Loading authority key certs
May 14 20:24:44.000 [notice] Bootstrapped 45%: Asking for relay descriptors
May 14 20:24:44.000 [notice] I learned some more directory information, but not enough to build a circuit: We need more microdescriptors: we have 0/6689, and can only build 0% of likely paths. (We have 0% of guards bw, 0% of midpoint bw, and 0% of exit bw = 0% of path bw.)
May 14 20:24:44.000 [notice] Bootstrapped 50%: Loading relay descriptors
May 14 20:24:45.000 [notice] Bootstrapped 56%: Loading relay descriptors
May 14 20:24:46.000 [notice] Bootstrapped 63%: Loading relay descriptors
May 14 20:24:46.000 [notice] Bootstrapped 70%: Loading relay descriptors
May 14 20:24:46.000 [notice] Bootstrapped 78%: Loading relay descriptors
May 14 20:24:46.000 [notice] Bootstrapped 80%: Connecting to the Tor network
May 14 20:24:47.000 [notice] Bootstrapped 85%: Finishing handshake with first hop
May 14 20:24:47.000 [notice] Bootstrapped 90%: Establishing a Tor circuit
May 14 20:24:48.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
May 14 20:24:48.000 [notice] Bootstrapped 100%: Done



```
and it stays like this with a process running tho, does that means I'm under tor till the terminal is open? I'd rather have tor as a stand alone browser.

I've only just realised my error deadflowr's pointed out, I was finally able to install it and run, thanks.

---

### Post by drvshrm on 2019-05-14
you can directly install it from ubuntu software center...just search tor browser and click on install...thats it...

---

### Post by yetimon_64 on 2019-05-14
> **moto1860 said:**
> ... I'd rather have tor as a stand alone browser....

If the stand alone browser is all you want I'd completely purge tor as supplied in the repos and use the tor browser bundle only as supplied by [noparse]torproject.org[/noparse] (url disabled).

Clicking on the tux icon at [[COLOR=#0000ff]--This link--[/COLOR]]("https://www.torproject.org/download/") will allow you to download the stand alone tor browser bundle. The link also supplies a pgp signature below the tux icon for checking your download. Extract the contents to where ever you wish to store it and enter the main directory extracted. Then click on "Tor browser setup", the set up icon will change to a launcher with the tor browser icon. Clicking the now set up new icon will actually launch the tor browser.

Using the tor browser bundle is very simple and it can be run either from your home directory on the HDD or from a USB stick etc. Just extract the installer to whatever location you want to run it from first. Once located and set up the browser can update itself from within the browser from that location, you don't need to download any further installers etc to update in the future.

---

