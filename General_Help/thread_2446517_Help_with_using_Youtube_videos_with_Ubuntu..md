---
title: "Help with using Youtube videos with Ubuntu."
date: 2020-07-01
forum: General Help
---

### Post by dlwy3k on 2020-07-01
Videos in YouTube and other places keep pausing every 5 - 10 seconds and may pause for  seconds or minutes.
I simply can not watch videos in Ubuntu 18.04.
I am a user. Know very little technical stuff.

Any help appreciated.
dlw

Using Hughes net.
Called them and they say there is not problem with reception.

System is Ubuntu 18.04 LTS
32gb ram, 250gb SSD.

HP Envy with 32" monitor.

---

### Post by QIII on 2020-07-02
Hello!

Two further bits of hardware information may be helpful:  The CPU and graphics.

Have you been able to use other OSes to get better reception/speed through HughesNet?  It would be difficult for a satellite internet provider to determine if you are having trouble with reception.  You might have trees in your LoS with the satellite.  The wind may be rocking the dish.  A pair of starlings may have nested on the receiver.  A wind storm may have knocked your dish out of alignment.

---

### Post by lvm on 2020-07-02
Note also that chromium does support hardware video acceleration on linux while firefox doesn't and is much more demanding to CPU.

---

### Post by ActionParsnip on 2020-07-02
What Web browser(s) have you tried? What video chip do you use?
If you run
```

sudo lshw -C display

```
What is the output?

---

### Post by Holger_Gehrke on 2020-07-02
Most streaming sites split the video into very many small blocks. If you use the 'Network Analysis' in the Firefox Web-developer Tools you'll see that they are about 5-10 seconds (a 48 second video on youtube I just checked this on got split into 10 small .webm files with sizes in the range of 100kb to 200kb). So I think the problem is not transmission speed but latency, the time between sending a request and receiving a reply.

Holger

---

### Post by sdsurfer on 2020-07-02
Hughes Net? I am so sorry . . . but it is probably the same situation I was in, there was nothing else available. Hughes Net will **always** tell you everything is fine and there were several lies I caught them in. Most horrible Internet experience ever for me. Wife also had an HP Envy for a few years, decent machine and should be able to handle this.

The problem with satellite internet is lag, around three seconds to make  the loop to space and back. I remember having to schedule that "last  second eBay bid" almost precisely three seconds from the closing bid  time so it would get in at the last second. At times the lag was worse  and I didn't get the bid in. They also demonstrated all sorts of DNS issues, including stealing the Internet Explorer "Not found" page for a DNS failure. I caught them in that one because I never used IE.

As suggested the first thing I would do is try different browsers, then a computer with a different operating system, over your connection. Always use a hard wired ethernet connection with satellite, WiFi only complicates the equation.

This could very well be the source of the problem, videos are transferred in blocks of data and they are not being moved fast enough to make the viewing seamless.

Edit: also supplement any further data you provide with an Internet Speed test from a couple sources, and what Hughes Net says you should be getting.

---

### Post by Yellow Pasque on 2020-07-02
> **lvm said:**
> Note also that chromium does support hardware video acceleration on linux while firefox doesn't and is much more demanding to CPU.

For the record, FF does support video accel in Wayland session: [https://www.phoronix.com/scan.php?page=news_item&px=Firefox-76-VA-API-Formats](https://www.phoronix.com/scan.php?page=news_item&px=Firefox-76-VA-API-Formats)

Oh, and you should edit out the first part of your comment before a forum staffer does it for you... [https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

---

### Post by dlwy3k on 2020-07-02
I hope this helps.

Intel Core i7-6700k CPU @ 4.00GHz x 8


Yellow Pasque,
Oh, and you should edit out the first part of your comment before a forum staffer does it for you..
I am not trying to download, just watching.

dlw@dlw-750:~$ sudo lshw -C display
[sudo] password for dlw: 
  *-display                 
       description: VGA compatible controller
       product: GM107 [GeForce GTX 745]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:131 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
dlw@dlw-750:~$

---

### Post by Yellow Pasque on 2020-07-02
> **dlwy3k said:**
> Yellow Pasque, I am not trying to download, just watching.

That was directed at the person/comment I quoted, not you.

Anyway, the i7-6700k CPU in question should be able to decode most, if not all, video smoothly without any help from GPU. I would suspect a connection/network issue too.

---

### Post by Skaperen on 2020-07-02
earth-orbit-earth latency is less than 650 milliseconds.  equipment can add a little more.  YouTube has a diagnostic tool that combined with tcpdump may show to someone what is happening.  right click in a video and select "Stats for nerds".  it will show the transfer of blocks of data and the buffer state.  unless someone else visits to help or you give up and switch to another OS, you will need to learn more to work with us to find out what is happening and who to blame.

in theory, a receiver can record signal levels and transfer activity and provide that to someone that knows how to ask for it.  i know of at least one cable provider that can do that.  i would expect satellite providers to do that.  i would be surprised if one has no such ability.

---

