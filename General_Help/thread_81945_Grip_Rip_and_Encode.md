---
title: "Grip Rip and Encode?"
date: 2005-10-25
forum: General Help
---

### Post by kimvall on 2005-10-25
Hello all, which of the encoder and rippers do you recommend using? I prefer an exact (as possible) result above speed, and I'm willing to pay for it (in minutes that is, not cash). ;-)

---

### Post by landotter on 2005-10-25
I think ripperX is the nicest balance of features/quality/ease of use that you'll find for Linux, but there are others. Grip isn't bad,but the UI is horrendous, KDE users have the very excellent kaudiocreator.

All are available via Synaptic.

---

### Post by kimvall on 2005-10-25
I was more thinking of which rip and encoding tool to use within Grip.

---

### Post by landotter on 2005-10-25
[quote=kimvall]I was more thinking of which rip and encoding tool to use within Grip.[/quote] 
for personal use, I use Vorbis at the "6" quality setting, but for sharing, I use the ubiquitous .mp3 format set at 196 CBR or similar. LAME is the best encoder imho, and used by most Linux ripper/encoders. It's available via Synaptic.

---

### Post by bionnaki on 2005-10-25
for mp3, use lame  --alt-preset standard %s %d or --alt-preset extreme %s %d
this is the best mp3 encoding, imho - avoid any other encoders & stick with lame.

for ogg, I just use the standard oggenc @ - q 6

---

### Post by Rebajas on 2005-11-13
I can't find lame in Synaptic? Is there something specific I should be searching for; I tried libmp3, lame and mp3 with no obvious results specifically for Lame.

I also tried 'sudo apt-get install lame' in my terminal but I got this error: 'Package lame has no installation candidate'.

I also tried installing from source but get to a certaim point and the install bombs out with 'permission denied whilst trying to create directory' errors?

Any ideas one way or the other would be useful?

R.

---

### Post by hw-tph on 2005-11-13
[QUOTE=Rebajas]I can't find lame in Synaptic? Is there something specific I should be searching for; I tried libmp3, lame and mp3 with no obvious results specifically for Lame.[/QUOTE]

Enable multiverse in your /etc/apt/sources.list, then execute **apt-get update** and **apt-get install lame**.


Håkan

---

