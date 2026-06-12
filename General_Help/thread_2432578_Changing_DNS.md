---
title: "Changing DNS"
date: 2019-12-04
forum: General Help
---

### Post by Frank_Snyder on 2019-12-04
I have a GUI iteration of 18.04 running as a full VM on my Proxmox host. This exist really for only one reason, so that I can have a centralized place to mount all my network locations and then have those backed up to crashplan (crasphlan doesn't support headless within linux)




I can change "/etc/resolv.conf" and it will instantly start using the DNS I point it to. The issue is when any kind of system reboot comes into play. Once recovered, it goes back to using the local host as the DNS.

It seems this is a byproduct of the network GUI features taking precedence? However, that section in my GUI appears to be blank (see attached pic "1").

I've tried setting it in /etc/network/interfaces as this is how I've configured all the other static options (see attached pic "2"). This however does nothing for the DNS.

Any ideas on how to set a DNS that will persist between system/service restarts?


**Edit**:

It seems resolvconf should be the service I need. Attempting to install it, I could see there were issues with dsnmasq trying to use the port (I assume part of the resolvconf service) but it was reported another service was already using port 53. Continued investigation showed this service to be systemd-resolved. I used[ these instructions]("https://gist.github.com/zoilomora/f7d264cefbb589f3f1b1fc2cea2c844c") to remove systemd-resolved and then used [these instructions]("https://datawookie.netlify.com/blog/2018/10/dns-on-ubuntu-18.04/") to deploy resolvconf.

I received no apparent errors when running this, however DNS is still not working (see attached pic "3")

[IMG]https://imgur.com/58c93ad0-2c1c-4987-a9d6-5f7492e0f375[/IMG]

---

### Post by DuckHook on 2019-12-04
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

### Post by Frank_Snyder on 2019-12-04
Sorry about that. I agree and would usually post direct terminal outputs but the issue is that the OS is within a console and is therefore harder to copy over unless I'm browsing the forums directly in the VM. I'll edit my post as you suggested.

---

### Post by SeijiSensei on 2019-12-04
I would learn to use systemd-resolved since it will be the standard in all future releases for some time to come.  You can specify particular DNS servers in the file /etc/systemd/resolved.conf. See "man resolved.conf" for details.

---

### Post by Frank_Snyder on 2019-12-04
Thanks for the reply. Now to figure out how to re-add it given I used link in above edit to remove it...

---

### Post by SeijiSensei on 2019-12-04
```

sudo apt update
sudo apt purge resolvconf
sudo apt install systemd-resolved

```
should do the trick.

---

### Post by Frank_Snyder on 2019-12-04
Hmm, I'm getting the "unable to locate package" when going to reinstall it. I have all the basic repositories enabled and a quick search did not seem to unveil what one would be holding this.

---

### Post by Quarkrad on 2019-12-05
I have the just the four main repositories (universe, restricted, multiverse and main (canonical-supported)) and resolvconf is available via Synaptic

---

### Post by webaake on 2019-12-05
The tested and true way was always to edit /etc/resolvconf/resolv.conf.d/tail , as it wouldn't be overwritten.

---

### Post by SeijiSensei on 2019-12-06
> **Frank_Snyder said:**
> Hmm, I'm getting the "unable to locate package" when going to reinstall it. I have all the basic repositories enabled and a quick search did not seem to unveil what one would be holding this.
Apparently systemd-resolved is not in its own package. You need to install the entire systemd package.

[https://packages.ubuntu.com/search?suite=bionic&arch=any&mode=exactfilename&searchon=contents&keywords=systemd-resolved](https://packages.ubuntu.com/search?suite=bionic&arch=any&mode=exactfilename&searchon=contents&keywords=systemd-resolved)

---

