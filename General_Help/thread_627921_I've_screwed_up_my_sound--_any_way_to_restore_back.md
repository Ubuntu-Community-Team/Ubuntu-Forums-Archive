---
title: "I've screwed up my sound-- any way to restore back to original state?"
date: 2007-11-30
forum: General Help
---

### Post by tdoggette on 2007-11-30
My sound card (integrated ICH9 HD Audio) was autodetected on install of 7.10 x64. The volume was low, though-- maximum volume was about decent listening volume. I followed the steps at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to try to make it louder, but it just killed my sound. The following is the error message up on testing using the Sound Preferences, in case it helps.
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.
```
How can I get my sound back to the way it was upon installation?

lshw reveals:
```
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
```

---

### Post by tdoggette on 2007-12-01
Does anyone have anything I could try, at least?

---

### Post by tdoggette on 2007-12-01
I hate to keep bumping, but it's been a few hours, and I really need help.

---

