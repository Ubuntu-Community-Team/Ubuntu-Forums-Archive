---
title: "About Linux command line"
date: 2021-08-26
forum: General Help
---

### Post by satimis on 2021-08-26
Hi all,

I combine multiple .wav files and then convert the output.wav to mp3 running;```

$ sox *.wav output.wav | ffmpeg -i output.wav -vn -ar 44100 -ac 2 -b:a 192k output.mp3

```
It works but generating an output.wav file. Please advise how to modify the command line without generating an output.wav file ? I only need output.mp3

Thanks

Regards

---

### Post by CharlesA on 2021-08-26
You could try it this way, but I have no idea if it will work or not.

```
sox *.wav | ffmpeg -i pipe:0 -vn -ar 44100 -ac 2 -b:a 192k output.mp3
```

[https://ffmpeg.org/ffmpeg-protocols.html#pipe](https://ffmpeg.org/ffmpeg-protocols.html#pipe)

---

### Post by vanadium on 2021-08-26
Something strange is being done here. You use the pipe symbol, so any terminal output of sox would go to ffmpeg, which, in turn, will read from standard input. Probably not an issue because ffmeg does not need user interaction. This construct, however, makes ffmpeg read the output.wav before it has been finalized by the first command. Apparently, however, "it works". Did you listen to the output file?

Use ";" instead, or perhaps better, "&&" which will cause the next command to proceed only when the first finished succesfully. That may already be enough to make ffmpeg encode as suggested by the extension of the output file.

---

### Post by Irihapeti on 2021-08-26
*Thread moved to **General Help** as it's a support question.*

---

### Post by satimis on 2021-08-26
Hi all,

Thanks for your advice.

Following command line works for me;```

$ sox *.wav output.wav ; ffmpeg -i ouput.wav -vn -ar 44100 -ac 2 -b:a 192k output.mp3 ; rm output.wav

```

Regards

---

### Post by satimis on 2021-08-26
Hi all,

Thanks for your advice.

Following command line works for me;```

$ sox *.wav output.wav ; ffmpeg -i ouput.wav -vn -ar 44100 -ac 2 -b:a 192k output.mp3 ; rm output.wav

```

Regards

---

### Post by andrew.46 on 2021-08-28
> **satimis said:**
> Please advise how to modify the command line without generating an output.wav file ? I only need output.mp3

This can be accomplished reasonably *elegantly* as follows:

```

sox *.wav -t wav - | lame -V 2 - output.mp3

```

I am not sure about the file ordering of the sox command though, perhaps this is not an issue with your input files?

---

### Post by satimis on 2021-08-30
> **andrew.46 said:**
> This can be accomplished reasonably *elegantly* as follows:

```

sox *.wav -t wav - | lame -V 2 - output.mp3

```

I am not sure about the file ordering of the sox command though, perhaps this is not an issue with your input files?
Hi,

Thanks for you advice which works for me here without generating output.wav file.

However I expect to learn how to fix file ordering.

Example:
File_1.wav File_2.wav File_3.wav File_4.wav File_5.wav File_6.wav
File_7.wav File_8.wav File_9.wav File_10.wav File_11.wav File_12.wav etc.

Can any folk on the forum help?  Thanks

Regards

---

### Post by Impavidus on 2021-08-30
The command line with *.wav uses shell globbing to get a list of filenames. The shell (bash) replaces the string *.wav with a list of all filenames in the current directory matching that pattern, alphabetically ordered, which is then passed to sox. And as 2 comes after 1, file_2.wav comes after file_10.wav. You can put all filenames on the command line yourself, in any order you like, but I think the easy solution is to rename the files so that those with lower numbers have a leading 0: file_01.wav ... file_09.wav file_10.wav etc.

Alternatively, use shell string expansion. file_{1..15}.wav will expand to file_1.wav file_2.wav ... file_15.wav.

---

### Post by satimis on 2021-08-30
> **Impavidus said:**
> The command line with *.wav uses shell globbing to get a list of filenames. The shell (bash) replaces the string *.wav with a list of all filenames in the current directory matching that pattern, alphabetically ordered, which is then passed to sox. And as 2 comes after 1, file_2.wav comes after file_10.wav. You can put all filenames on the command line yourself, in any order you like, but I think the easy solution is to rename the files so that those with lower numbers have a leading 0: file_01.wav ... file_09.wav file_10.wav etc.

Alternatively, use shell string expansion. file_{1..15}.wav will expand to file_1.wav file_2.wav ... file_15.wav.
Thanks for your advice.

Performed following tests

$ ls```

Track12.wav  Track3.wav  Track6.wav  Track9.wav
Track10.wav            Track1.wav   Track4.wav  Track7.wav
Track11.wav            Track2.wav   Track5.wav  Track8.wav

```

1)
$ sox 'file_{Track1 Track2 Track3 Track4 Track5 Track6 Track7 Track8 Track9 Track10 Track11 Track12}.wav' -t wav - | lame -V 2 - output.mp3```

sox FAIL formats: can't open input file `file_{Track1 Track2 Track3 Track4 Track5 Track6 Track7 Track8 Track9 Track10 Track11 Track12}.wav': No such file or directory
Warning: unsupported audio format
Can't init infile '-'

```

2)
$ sox file_{Track1 Track2 Track3 Track4 Track5 Track6 Track7 Track8 Track9 Track10 Track11 Track12}.wav -t wav - | lame -V 2 - output.mp3```

sox FAIL formats: can't open input file `Track12}.wav': No such file or directory
Warning: unsupported audio format
Can't init infile '-'

```

3)
$ sox Track_{1 2 3 4 5 6 7 8 9 10 11 12}.wav -t wav - | lame -V 2 - output.mp3```

sox FAIL formats: can't open input file `12}.wav': No such file or directory
Warning: unsupported audio format
Can't init infile '-'

```

Still fail

Regards

---

### Post by Impavidus on 2021-08-30
Try```
sox Track_{1..12}.wav -t wav - | lame -V 2 - output.mp3
```

---

### Post by satimis on 2021-08-31
> **Impavidus said:**
> Try```
sox Track_{1..12}.wav -t wav - | lame -V 2 - output.mp3
```
$ sox Track_{1..12}.wav -t wav - | lame -V 2 - output.mp3```

sox FAIL formats: can't open input file `Track_12.wav': No such file or directory
Warning: unsupported audio format
Can't init infile '-'

```

**$ sox Track{1..12}.wav -t wav - | lame -V 2 - output.mp3**
It works.  Files in ordering

Thanks

Regards

---

