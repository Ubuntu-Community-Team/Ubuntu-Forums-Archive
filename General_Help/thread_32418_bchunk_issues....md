---
title: "bchunk issues..."
date: 2005-05-07
forum: General Help
---

### Post by Tir on 2005-05-07
I've been attempting to convert a .bin/.cue pair into a .iso by using bchunk. My efforts have been for naught. Everytime I attempt to convert, bchunk gives me the same spiel...

I type in *bchunk file name.bin file name.cue file name*. Then I get this:

```
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
        Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
        partly based on his Pascal (Delphi) implementation.
        Support for MODE2/2352 ISO tracks thanks to input from
        Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
        and Matthew Green <mrg@eterna.com.au>.
        Released under the GNU GPL, version 2 or later (at your option).

Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo
  -v  Verbose mode
  -r  Raw mode for MODE2/2352: write all 2352 bytes from offset 0 (VCD/MPEG)
  -p  PSX mode for MODE2/2352: write 2336 bytes from offset 24
      (default MODE2/2352 mode writes 2048 bytes from offset 24)
  -w  Output audio files in WAV format
  -s  swabaudio: swap byte order in audio tracks

```

What am I doing wrong?

---

### Post by JonahRowley on 2005-05-08
> I type in bchunk file name.bin file name.cue file name
> Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo

You have spaces in your filenames, which won't work unless quoted.  Use:
```
bchunk "file name.bin" "file name.cue" "file name"
```

Or, if that's not the problem, try posting the exact command you tried.

---

### Post by Tir on 2005-05-08
-Edit-

Problem solved. I just used K3B instead.

---

