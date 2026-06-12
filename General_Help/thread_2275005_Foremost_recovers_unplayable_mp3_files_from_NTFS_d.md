---
title: "Foremost recovers unplayable mp3 files from NTFS dd image"
date: 2015-04-23
forum: General Help
---

### Post by user155478 on 2015-04-23
So I uncommented the lines in the **/etc/foremost.conf** that are associated with mp3s. And initiated the following command:  

```
foremost -i windows_recovery_ddrescue.img -o /media/john/partition/recovery
```

And it did recover 15 ***.mp3** files, but the problem is that none of them is playable by a media player. What's also strange, is that 13 of those 15 recovered ***.mp3** files are all 8 MB sized - precisely 8,0 MB. And the two remaining are 4,4 MB and 3,5 MB.  These 15 files are from a collection of 40 **mp3** files. Here's are example headers of some of the **mp3** files from the collection:
```
hexdump -n 15 file1.mp3
0000000 fbff 6490 0000 0000 0000 0000 0000 0000
```
```
hexdump -n 15 file2.mp3
0000000 4449 0333 0000 0000 761f 0000 0000 0000
```
```
hexdump -n 15 file3.mp3
0000000 4449 0233 0000 0000 4c11 5454 0032 0000
```

Therefore I modified the config file and added those header values to the file. Here's the final result of the **mp3** lines in conf file:
```
        mp3     n       31457280 \xFF\xFB??\x44\x00\x00
        mp3     n       31457280 \x57\x41\x56\45            \x00\x00\xFF\
        mp3     n       31457280 \xFF\xFB\xD0\            \xD1\x35\x51\xCC\
        mp3     n       31457280 \x49\x44\x33\
        mp3     n       31457280 \x4C\x41\x4D\x45\
        mp3     n       31457280 \xfb\xff\x64\x90
        mp3     n       31457280 \xfb\xff\x64\x90\
        mp3     n       31457280 \x44\x49\x02\x33
        mp3     n       31457280 \x44\x49\x02\x33\
```


Then it recovered 37 ***.mp3** files of which none are playable by VLC. 28 files out of 37 are with size 31,5 MB.

So... I've got 37 broken files. Is it something I did wrong with the command or editing the config file? Or Foremost just isn't capable of recovering ***.mp3** files? Because it did great with recovering ***.jpg** files.

Help anyone? :)

---

### Post by dragonfly41 on 2015-04-23
My understanding is that foremost does not support mp3 recovery ...

[http://ubuntuforums.org/showthread.php?t=1321051](http://ubuntuforums.org/showthread.php?t=1321051)

[http://forums.bodhilinux.com/index.php?/topic/6728-foremost-question/](http://forums.bodhilinux.com/index.php?/topic/6728-foremost-question/)

but you can try photorec ...

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

---

