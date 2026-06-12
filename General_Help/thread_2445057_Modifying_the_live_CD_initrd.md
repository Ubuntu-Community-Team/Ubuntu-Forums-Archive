---
title: "Modifying the live CD initrd"
date: 2020-06-08
forum: General Help
---

### Post by harisund2 on 2020-06-08
I want to create a custom splash screen for a live CD. From what I understand, this is something that needs modification in <cd rom>/casper/initrd

The wiki pages for live cd customization and live cd customization from scratch are woefully out of date. 

The initrd for ubuntu 20 has 2 microcode patches, followed by the actual ram disk. You can use tools like "binwalk" or "lsinitramfs" to see the contents, or "unmkinitramfs" to extract it. 

Fine. So I extracted it. I see 3 folders, two with microcodes, one with the actual file system. Let's say I make a change in the file system. All fine so far. 

Now how do I create a new initrd again? How do "I" compress the 3 folders (file system, microcode, microcode) into a new initrd for my new live CD? 

Basically there is no "re-initramfs". There is a "mkinitramfs" but that doesn't do what we are trying to do here. 

Any thoughts?

---

### Post by tea for one on 2020-06-09
You may wish to explore Cubic.

[https://launchpad.net/cubic](https://launchpad.net/cubic)

Possibly the following link in their **Answers** will provide a clue.

[https://answers.launchpad.net/cubic/+question/691183](https://answers.launchpad.net/cubic/+question/691183)

---

