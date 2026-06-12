---
title: "bash + flac/aac decoder help"
date: 2007-11-28
forum: General Help
---

### Post by psuman on 2007-11-28
Wasn't sure where to post this, but I figured this would be a good place to start.  I'm currently trying to use x360mediaserve to share my music collection with my xbox360.  WMA and MP3 files work fine, but anything that needs to be transcoded (i.e. flac and aac files) have been giving me a bit of a headache.  I've managed to trace the problem back to spaces in my collections filenames.  

Unfortunately, the bash scripts that come with x360media serve do not play nice with spaces in filenames, so I've been trying to rewrite them so they escape the filenames before passing them to the decoder.  Here's where things get a bit hairy.  For whatever reason, when I pass the properly escaped filename to flac as a string, flac treats it as a series of files instead of a single file.  Any help would be **greatly** appreciated here... I'm starting to lose my sanity.

flacpcm:
```

#!/bin/bash
var=$@
var="${var//\ /\\ }"

#echo for testing purposes
echo $var
echo "flac -d $var -c --endian=big --force-raw-format --sign=signed"
echo "------------------------"
flac -d $var -c --endian=big --force-raw-format --sign=signed

```

Output from /flacpcm 05 - Mr. Genius.flac:
> 
05\ -\ Mr.\ Genius.flac
flac -d 05\ -\ Mr.\ Genius.flac -c --endian=big --force-raw-format --sign=signed
------------------------
flac: invalid option -- \


When I copy the flac -d... line and run it directly from a bash shell it dumps the pcm into stdout (which is what I want the script to do)

---

### Post by nick_h on 2007-11-28
Have you tried enclosing the $var variable in quotes?

---

### Post by psuman on 2007-11-28
yeap, if I do that I get this garbage:

```

flac 1.1.4, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.


05: ERROR initializing decoder
    init status = FLAC__STREAM_DECODER_INIT_STATUS_ERROR_OPENING_FILE

An error occurred opening the input file; it is likely that it does not exist
or is not readable.

Mr.: ERROR initializing decoder
     init status = FLAC__STREAM_DECODER_INIT_STATUS_ERROR_OPENING_FILE

An error occurred opening the input file; it is likely that it does not exist
or is not readable.

Genius.flac": ERROR initializing decoder
              init status = FLAC__STREAM_DECODER_INIT_STATUS_ERROR_OPENING_FILE

An error occurred opening the input file; it is likely that it does not exist
or is not readable.

```

And again, if I enter the "flac -d... " line that the script would be running at a bash prompt it works perfectly.

---

### Post by nick_h on 2007-11-29
Did you remove the escaped spaces from the variable?

You should need:
```
flac -d -c --endian=big --force-raw-format --sign=signed "$var"
```
The contents of $var does not need the backslashes.

---

### Post by psuman on 2007-11-29
that worked, thanks

---

