---
title: "Command to create ISO on music files"
date: 2024-05-14
forum: General Help
---

### Post by satimis on 2024-05-14
Hi all,

```

$ cat /dev/scd0 > ~/music.iso
```
can create ISO on CD

What will be the command to create ISO on music files .wav ?  The ISO created can be used to burn new music CD.

Thanks in advance.

Regards

---

### Post by Dennis N on 2024-05-14
> **satimis said:**
> Hi all,

```

$ cat /dev/scd0 > ~/music.iso
```
can create ISO on CD

What will be the command to create ISO on music files .wav ?  The ISO created can be used to burn new music CD.

Thanks in advance.

Regards
for a directory, or separate files:
```
genisoimage -o isoname.iso directory
genisoimage -o isoname.iso file1 file2 file3
```

---

### Post by satimis on 2024-05-14
> **Dennis N said:**
> for a directory, or separate files:
```
genisoimage -o isoname.iso directory
genisoimage -o isoname.iso file1 file2 file3
```
Hi@Dennis,

Thanks for your advice.

$ apt policy genisoimage```

genisoimage:
  Installed: (none)
  Candidate: 9:1.1.11-3.4
  Version table:
     9:1.1.11-3.4 500
        500 http://hk.archive.ubuntu.com/ubuntu mantic/main amd64 Packages

```
It is on REPO.

Can I run "cat" to do the job?  Thanks

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
To burn music.iso on cd, run on Terminal```

dd if=~/path/image.iso of=/dev/cdrom

```
Is it correct ?

---

### Post by Dennis N on 2024-05-14
You wrote:
> The ISO created can be used to burn new music CD.
I assume by music CD you mean an audio CD.

Answer:
Maybe. There are command line utilities to burn audio CDs from .wav files. But, if the .wav files are inside an iso, can the burner utility read the contents of an .iso? I'm not sure about that. 

I looked for a guide, and here is one (but not from an iso source):

[Using the command line to burn music to an audio CD]("https://linuxconfig.org/burn-your-music-files-from-any-format-to-audio-cd-using-command-line")

dd command would not make an audio CD, just a exact copy of the iso.

---

### Post by satimis on 2024-05-15
> **Dennis N said:**
> You wrote:

I assume by music CD you mean an audio CD.

Yes, correct.

> 
Answer:
Maybe. There are command line utilities to burn audio CDs from .wav files. But, if the .wav files are inside an iso, can the burner utility read the contents of an .iso? I'm not sure about that. 

I looked for a guide, and here is one (but not from an iso source):

[Using the command line to burn music to an audio CD]("https://linuxconfig.org/burn-your-music-files-from-any-format-to-audio-cd-using-command-line")

dd command would not make an audio CD, just a exact copy of the iso.
Thanks for your advice.

It is for curiosity to start this thread. Actually audio.iso is not much use.  I would stop here.

Regards

---

