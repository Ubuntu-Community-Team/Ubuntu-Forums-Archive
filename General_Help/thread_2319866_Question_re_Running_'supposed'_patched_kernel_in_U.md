---
title: "Question re: Running 'supposed' patched kernel in Ubuntu 14.04.2 LTS"
date: 2016-04-08
forum: General Help
---

### Post by bra|10n on 2016-04-08
Thanks for taking the time to read this post...

[U]Background

[/U]I started with an iso image found[ here]("http://liliputing.com/2015/07/install-ubuntu-14-04-lts-on-the-2gb-intel-compute-stick.html") of Ubuntu 14.04 LTS to run on an Intel Compute Stick [STCK1A32WFC]("http://www.intel.com/buy/us/en/product/desktop/intel-stck1a32wfc-499746#tech_specs") which originally shipped with Win8.1 upgradable to Win10. To cut a long story short, Ubuntu (kernel?) does not include driver support for WIFI, Bluetooth or Sound via HDMI on the ICS so the need to use _that_ iso which apparently includes a patched kernel and so far all is working perfectly fine.

I've been kicking around on this setup now for little over a week and it is surprisingly cute despite it's limitations. 

What I don't understand though is how after applying updates including to the kernel, how WIFI and Sound etc continue to work. 
If I understand this all correctly, moving to a different kernel should cause this hardware issues?

The installation iso came with 3.16.30-generic and after updating to 3.16.69 generic post install, and again today to 3.16.70-generic everything is working. Is this because all of these are 3.16 kernels or is it because drivers for the said hardware were included in the iso? I ask because I want to know a) what I should and shouldn't do if a new series kernel comes along, and b) what situation(s) I might find myself in down the track.

Any help is greatly appreciated...

---

