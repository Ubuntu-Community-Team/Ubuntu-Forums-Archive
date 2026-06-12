---
title: "extract subtitles with mkvmerge"
date: 2022-06-02
forum: General Help
---

### Post by demonenero84 on 2022-06-02
So I have this mkv file called movie.mkv :)
if i run the command "[FONT=monospace][COLOR=#000000]mkvmerge -i movie.mkv" I get
[/COLOR][/FONT]> [FONT=monospace][COLOR=#000000]File 'movie.mkv': container: Matroska [/COLOR]
Track ID 0: video (AVC/H.264/MPEG-4p10) 
Track ID 1: audio (AAC) 
Track ID 2: subtitles (VobSub) 
Chapters: 5 entries 
Global tags: 1 entry 
Tags for track ID 0: 1 entry 
Tags for track ID 1: 1 entry 
Tags for track ID 2: 1 entry [/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000]
How can I extract subtitles?
I took a look here
[https://askubuntu.com/questions/452268/extract-subtitle-from-mkv-files](https://askubuntu.com/questions/452268/extract-subtitle-from-mkv-files)
but this solution does not work for me
thanks a lot in advance
[/COLOR][/FONT] 

[/FONT]

---

### Post by #&amp;thj^% on 2022-06-02
This should still work: [https://keevi.io/learn/extract-subtitles-from-mkv](https://keevi.io/learn/extract-subtitles-from-mkv)

---

### Post by TheFu on 2022-06-02
**mkvmerge -i** isn't correct.  mkvmerge supports the **-o** option for the output, not input.

Use 
```
$ mkvextract tracks movie.mkv 2:movie.sub
```
The numbering of the tracks can be off by 1 ... but I think 2: is correct.

Use **mkvinfo movie.mkv** to get the track number for each different track inside the MKV container.

Multiple tracks can be pulled concurrently.

---

### Post by demonenero84 on 2022-06-02
thanks the first solution did the trick (the GUI program is windows only but It runs fine with wine)

---

