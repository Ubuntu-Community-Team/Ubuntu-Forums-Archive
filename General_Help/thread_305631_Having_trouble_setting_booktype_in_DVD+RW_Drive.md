---
title: "Having trouble setting booktype in DVD+RW Drive"
date: 2006-11-23
forum: General Help
---

### Post by misterbeetz on 2006-11-23
Does anyone know how to set the booktype of a dvd burner that dosent get detected by the following bitsetting command?:

 # dvd+rw-booktype -dvd-rom -unit+r /dev/hdd

I get the following response:

This program targets units of RICOH, BENQ, BTC, LITE-ON, LG and PLEXTOR designs. /dev/hdc doesn't appear to be one. Exiting.

However when I enter an inquiry of what the drive is with dvd+rw-mediainfo /dev/hdc, i get the following response:

INQUIRY:       [LITE-ON ][DVDRW SHW-160P6S][PS08]

... along with the info of the inserted media.  So clearly the drive is a lite-on which I know works. Any other bitsetting windows utilities i have tried using wine also claim that a lite-on drive cannot be found.

Does anyone know whats going on and how i might be able to remedy this?  Any help would be much appreciated.

- misterbeetz

---

### Post by misterbeetz on 2006-11-24
Turns out that the bittsetting command requires the sudo prefix.  Everything is working now! :-)

- misterbeetz

---

