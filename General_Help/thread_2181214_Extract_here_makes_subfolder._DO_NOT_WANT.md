---
title: "Extract here makes subfolder. DO NOT WANT"
date: 2013-10-16
forum: General Help
---

### Post by edward-holystone on 2013-10-16
Someone please help me. I have 300 archives that I need to extract. The files inside are loose files and the archiver should be extracting them loose.
Instead it extracts them into a subfolder. It's a miracle I haven't started crying yet. Please help.

To elaborate, I am selecting all the files, right clicking and pressing "extract here." When I do that, it extracts the files into subfolder rather than directley into the folder I want them in.

---

### Post by nerdtron on 2013-10-17
hmm... try a script to extract each folder.
Are your archives sequential in names? that would be better. I assume you have the following names
sample directory structure:
```
nerdtron@node175:~/main_folder$ ls
archive10.tgz  archive2.tgz  archive4.tgz  archive6.tgz  archive8.tgz
archive1.tgz   archive3.tgz  archive5.tgz  archive7.tgz  archive9.tgz
extract.sh

```

We want to extract all those archives to main folder and not create any subfolders right?
```
 cd /path/to/the/archives
nano extract.sh 
```
Paste the following, and then save and exit the editor.
```

#!/bin/bash
for archive in  *.tgz                  ##list all archives for loop
do
tar -zxvf "$archive"                   ##extract the archive
dirname="${archive%%.*}"         ##get the name of the created subfolder
  mv  "$dirname"/* .                  ##move all contents of the subfolder up to the current directory
done
```

Run the script.
```
bash extract.sh 
```

After extraction, there will still be subfolders but they won't contain any file cause you already moved them on the script.

---

### Post by Vaphell on 2013-10-17
sounds like a non issue.

1. extract here with subfolders
2. mv /dir/*/* -t /dir
3. delete empty subdirs

---

### Post by edward-holystone on 2013-10-17
I'm not exactly certain what you're telling me to do. These are all the archives, I want to extract the loose files inside to a folder named "songs" located at /home/edward/downloads/songs. Yes this is Ubuntu, it just looks different because I mess around with it a lot.

[IMG]http://i.imgur.com/KCdHosi.png[/IMG]

[IMG]http://i.imgur.com/oVkXeBk.png[/IMG]

[IMG]http://i.imgur.com/UeopTf5.png[/IMG]

---

### Post by The Spectre on 2013-10-17
Give PeaZip a try...
[http://peazip.sourceforge.net/peazip-linux.html](http://peazip.sourceforge.net/peazip-linux.html)

You can Download the portable version so you don't even have to install it to try it out.

---

### Post by Vaphell on 2013-10-17
i am telling you should extract the files either way because gathering them in one place is a rather trivial task
just give correct paths/dir names so you can get your short terminal command that will do it in 1 second.

it will be along the lines of
```
mv -t . ./*/*
```

---

### Post by edward-holystone on 2013-10-17
What am I supposed to write in place of the periods and asterisks?
Sorry if I'm being difficult, but this makes no sense to me:
mv -t . ./*/*

---

### Post by philinux on 2013-10-17
Found this 

```
for i in *.tar.gz; do tar xvzf $i -C path/to/output/directory; done
```

from here [http://stackoverflow.com/questions/5177762/ubuntu-extract-multiple-tar-gz-files-to-new-directory](http://stackoverflow.com/questions/5177762/ubuntu-extract-multiple-tar-gz-files-to-new-directory)

I would move a couple of archives to a test directory and try it out first.

---

### Post by Vaphell on 2013-10-17
> **edward-holystone said:**
> What am I supposed to write in place of the periods and asterisks?
Sorry if I'm being difficult, but this makes no sense to me:
mv -t . ./*/*

. is current dir * matches anything
post your directories so you get a ready to use command

either way looking at the screenshots
ctrl+alt+t to open terminal

```
cd ~/Downloads/*Beatmap*100
```
enter your_home_dir/Downloads/<something>Beatmap<something>100, if the name is unique and matching, the shell should resolve it despite * wildcards. Had to use wildcards because the full name is not visible in the screenshots

```
mv -t . ./*/*
```
move all files from subdirs ( [COLOR="#0000FF"].[/COLOR]/[COLOR="#008000"]*[/COLOR]/[COLOR="#4B0082"]*[/COLOR] = [COLOR="#0000FF"]current dir[/COLOR]/[COLOR="#008000"]subdirs with any name (all)[/COLOR]/[COLOR="#4B0082"]everything with any name[/COLOR] to a target dir . (current)

```
cd ../*Beatmap*200
```
go up 1 level (Downloads, ..=parent dir) and down to <something>Beatmap<something>200

```
mv -t . ./*/*
```
again move anything from subdirs to the top/current directory

```
cd ../*Beatmap*300
```
enter parent_dir/<something>Beatmap<something>300

```
mv -t . ./*/*
```
move stuff



this should move all the files from the extraction dirs to their respective master dir
extract one rar and check if the relevant pair of commands works
you can copy paste these commands one by one by highlighting here and middleclicking in terminal to paste or with ctrl+c/ctrl+shift+v

---

### Post by edward-holystone on 2013-10-17
OK I give up with. 

These three folders contain the subfolders inside of which the loose files are located:
/home/edward/Documents/Beatmap1
/home/edward/Documents/Beatmap2
/home/edward/Documents/Beatmap3

I want to move the loose files inside the subfolders into this folder:
/home/edward/Documents/Songs

The subfolders are called "Beatmap Pack #001" All the way to "Beatmap Pack #300"
The loose files in each subfolder have completley random names, starting with different numbers, letters and symbols.

---

### Post by edward-holystone on 2013-10-17
BUMB!

Can someone please give me the commands please.

---

### Post by sandyd on 2013-10-17
> **edward-holystone said:**
> OK I give up with. 

These three folders contain the subfolders inside of which the loose files are located:
/home/edward/Documents/Beatmap1
/home/edward/Documents/Beatmap2
/home/edward/Documents/Beatmap3

I want to move the loose files inside the subfolders into this folder:
/home/edward/Documents/Songs

The subfolders are called "Beatmap Pack #001" All the way to "Beatmap Pack #300"
The loose files in each subfolder have completley random names, starting with different numbers, letters and symbols.
```

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

```
try
```

cd /home/edward/Documents/Beatmap1
mkdir tmp
unrar e *rar tmp
find tmp -type f -print0 | xargs -0 mv -t  /home/edward/Documents/Songs

```i would test with a few files first

---

### Post by mc4man on 2013-10-17
maybe just not use "extract here" from the context menu, instead right click on an archive > Open with Archive Manager, then click on the Extract button in the toolbar
The pop up screen should be self explanatory, in your case **Do uncheck** "Keep directory structure" under "Actions"

---

### Post by edward-holystone on 2013-10-17
> **Vaphell said:**
> . is current dir * matches anything
post your directories so you get a ready to use command

either way looking at the screenshots
ctrl+alt+t to open terminal

```
cd ~/Downloads/*Beatmap*100
```
enter your_home_dir/Downloads/<something>Beatmap<something>100, if the name is unique and matching, the shell should resolve it despite * wildcards. Had to use wildcards because the full name is not visible in the screenshots

```
mv -t . ./*/*
```
move all files from subdirs ( [COLOR=#0000FF].[/COLOR]/[COLOR=#008000]*[/COLOR]/[COLOR=#4B0082]*[/COLOR] = [COLOR=#0000FF]current dir[/COLOR]/[COLOR=#008000]subdirs with any name (all)[/COLOR]/[COLOR=#4B0082]everything with any name[/COLOR] to a target dir . (current)

```
cd ../*Beatmap*200
```
go up 1 level (Downloads, ..=parent dir) and down to <something>Beatmap<something>200

```
mv -t . ./*/*
```
again move anything from subdirs to the top/current directory

```
cd ../*Beatmap*300
```
enter parent_dir/<something>Beatmap<something>300

```
mv -t . ./*/*
```
move stuff



this should move all the files from the extraction dirs to their respective master dir
extract one rar and check if the relevant pair of commands works
you can copy paste these commands one by one by highlighting here and middleclicking in terminal to paste or with ctrl+c/ctrl+shift+v


IT WORKED

Thanks for the help, you're a life saver.

---

