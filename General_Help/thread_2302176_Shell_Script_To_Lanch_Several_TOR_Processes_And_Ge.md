---
title: "Shell Script To Lanch Several TOR Processes And Generate Web Traffic"
date: 2015-11-08
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-11-08
Hello,

I want to create a script that will launch several TOR processes and then generate multiple web searches or other traffic to better mask my real data stream. Can anyone give me some hints about how this could be done?

I am hoping to create something like the following:

```
#!/bin/sh
tor
sleep 1
tor
sleep 1
tor
sleep 1
tor
sleep 1
tor
sleep 1
tor
sleep 1
tor
sleep 5
tor
sleep 1
tor
sleep 1
tor
sleep 1
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2
firefox
sleep 2

generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic
generate search traffic

```

I know there's an xscreensaver hack called webcollage that generates traffic; but I don't want to actually display the screensaver; and I'd like to be able to configure the parameters of the search, so it looks more like my normal data stream. The same goes for the extra firefox processes.

Thanks, Hannibal

---

### Post by Lars Noodén on 2015-11-14
Why not use the Tor Browser Bundle and launch that several times?  (Though I don't see why multiple instances would help.)  The TBB has had a lot of polish put into making the browser fingerprint not stand out.  By running your own customized version of Firefox, you will be off a little and thus stand out uniquely.

---

### Post by coljohnhannibalsmith on 2015-11-14
> **Lars Noodén said:**
> Why not use the Tor Browser Bundle and launch that several times?  (Though I don't see why multiple instances would help.)  The TBB has had a lot of polish put into making the browser fingerprint not stand out.  By running your own customized version of Firefox, you will be off a little and thus stand out uniquely.

Can I pass command-line arguments to the Tor Browser Bundle?

---

### Post by Lars Noodén on 2015-11-15
Yes.  It's just a highly tuned Firefox.  So the same options should work.

However, I am not sure of how to get an overview of all of Firefox's options.  Neither the manual page nor the --help output show all the options.

---

### Post by coljohnhannibalsmith on 2015-11-15
> **Lars Noodén said:**
> Yes.  It's just a highly tuned Firefox.  So the same options should work.

However, I am not sure of how to get an overview of all of Firefox's options.  Neither the manual page nor the --help output show all the options.

Also, can I point "SurfRaw" @ TOR Browser Bundle?

---

### Post by Lars Noodén on 2015-11-16
If you can point it at regular Firefox, then you can probably point it at the TBB.  You'd have to give it a try.  The Tor Browser Bundle is easy to download, verify, and unpack.

---

