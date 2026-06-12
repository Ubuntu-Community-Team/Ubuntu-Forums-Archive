---
title: "How to batch convert some video files ?"
date: 2018-06-09
forum: General Help
---

### Post by linuxyogi on 2018-06-09
Previously [I asked]("https://ubuntuforums.org/showthread.php?t=2354289") how to encode a video file by simply copying the video codec and change the audio to mp3.

Now I want to do the same thing but _**batch encode**_.

There are several video files in a folder.

I want to encode them all by copying the video codec and change the audio to mp3.

Please give me the exact ffmpeg command.

A GUI will be really useful. Please tell me if there is one.

---

### Post by Holger_Gehrke on 2018-06-09
For GUI there's Handbrake and WinFF, both are in the repositories. On the command line, doing things in batches is the job of the shell not the applications, so something like
```

for i in LIST_OF_FILENAMES_SEPARATED_BY_SPACES ; do ffmpeg -i "$i" -vcodec copy -acodec mp3 "${i%.mkv}_mp3.mkv" ; done
``` would take a LIST OF FILENAMES SEPARATED BY SPACES and do the conversion on each of them, naming the resulting files like the source files but with '_mp3' inserted into the name before the extension. You can of course use wildcards in the list, they get expanded to a list of file names by the shell.

Holger

---

### Post by linuxyogi on 2018-06-09
> **Holger_Gehrke said:**
> For GUI there's Handbrake and WinFF, both are in the repositories. On the command line, doing things in batches is the job of the shell not the applications, so something like
```

for i in LIST_OF_FILENAMES_SEPARATED_BY_SPACES ; do ffmpeg -i "$i" -vcodec copy -acodec mp3 "${i%.mkv}_mp3.mkv" ; done
``` would take a LIST OF FILENAMES SEPARATED BY SPACES and do the conversion on each of them, naming the resulting files like the source files but with '_mp3' inserted into the name before the extension. You can of course use wildcards in the list, they get expanded to a list of file names by the shell.

Holger

I have installed WinFF but it won't let me copy the video. Can you please check for me ?

---

### Post by Holger_Gehrke on 2018-06-09
Of course WinFF can do it, but you've got to set up your own profile for the job (menu->edit->profile).

Holger

---

### Post by linuxyogi on 2018-06-09
> **Holger_Gehrke said:**
> Of course WinFF can do it, but you've got to set up your own profile for the job (menu->edit->profile).

Holger

When I go to Edit > Presets ... I get this  

[ATTACH=CONFIG]280048[/ATTACH]
(Click to enlarge)


```
 ffmpeg -i input.mkv -vcodec copy -acodec mp3 output.mkv 
```

^^ This is the command I use to convert the files.

What should I enter in the Presets window ?

---

### Post by Holger_Gehrke on 2018-06-09
The first, second and last field are just window dressing, filename for the preset (or "Profil", as the German translation calls them), a description and a category to put the preset into. Put something meaningful in them so you can find the preset again. The third field should have all the options but not the '-i', the input file name and the output file name, so in your case it should be '-vcodec copy -acodec mp3'. The fourth field is the extension of the output file name without a leading '.', so 'mkv' should go in there.

Holger

---

### Post by linuxyogi on 2018-06-09
> **Holger_Gehrke said:**
> The first, second and last field are just window dressing, filename for the preset (or "Profil", as the German translation calls them), a description and a category to put the preset into. Put something meaningful in them so you can find the preset again. The third field should have all the options but not the '-i', the input file name and the output file name, so in your case it should be '-vcodec copy -acodec mp3'. The fourth field is the extension of the output file name without a leading '.', so 'mkv' should go in there.

Holger

[ATTACH=CONFIG]280062[/ATTACH]

I did it like that ^^ and now its working. Thanks a lot.

---

