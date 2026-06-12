---
title: "unzip program"
date: 2013-01-23
forum: General Help
---

### Post by brain7734 on 2013-01-23
Hi everybody! I have tried to extract numerous zip files thru archive manager, but I  always get the same message 'command line output error'. It says it can not find zipfile directory. Is this an archive manager problem, and if so, what is a good alternative?

---

### Post by CharlesA on 2013-01-23
Could be a problem with the archive.

Have you tried 7zip?

---

### Post by brain7734 on 2013-01-23
If I download another unzip program, I need archive manager to unzip it, since this is the only program I have. Can I do it thru the terminal? Will it need to be unzipped? I'm not too familiar with zip and RAR files, so excuse my ignorance. Also, I'm trying to play Morrowind, specifically the Construction Set, and Wine does not seem to be working, either. Any suggestions?

---

### Post by omeomi on 2013-01-23
Which command did you use to unzip?

Did you install this?
```
sudo apt-get install unzip
```

---

### Post by SeijiSensei on 2013-01-23
RAR is a different animal from other compression algorithms because it is patented.  As a result the rar/unrar programs can only be installed from [restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats"). Sometimes I have to install unrar manually with "sudo apt-get install unrar".  Once that's done, the usual archive managers like Ark have no problem with RAR files.

---

### Post by brain7734 on 2013-01-23
Well, I've installed the unzip program thru the terminal, but I still can not unzip the file. I removed 'archive manager' and re-installed it, but  still the problem persists.

---

### Post by CharlesA on 2013-01-23
Try 7 zip (it's in the repos) and try again.

If you still cannot unpack the archive, it is likely corrupted.

---

### Post by prodigy_ on 2013-01-23
> **brain7734 said:**
> Can I do it thru the terminal?
```
unzip /path/to/archive_file
```

---

### Post by brain7734 on 2013-01-23
I'm obviously missing something. I can't download another unzip program like 7zip because I need to uncompress it, but the 'archive manager' can't uncompress the program. If it did work, I wouldn't need to download another unzip program in the first place. Anybody know what I'm missing? Any help would be greatly appreciated!

---

### Post by brain7734 on 2013-01-23
Yes, I tried this. "cannot find or open /path/to/archive_file, /path/to/archive_file.zip or /path/to/archive_file.ZIP."

---

### Post by lisati on 2013-01-23
> **brain7734 said:**
> I'm obviously missing something. I can't download another unzip program like 7zip because I need to uncompress it, but the 'archive manager' can't uncompress the program. If it did work, I wouldn't need to download another unzip program in the first place. Anybody know what I'm missing? Any help would be greatly appreciated!
How are you trying to install 7zip? The apt-get method previously mentioned should work.
> **brain7734 said:**
> Yes, I tried this. "cannot find or open /path/to/archive_file, /path/to/archive_file.zip or /path/to/archive_file.ZIP."
You need to replace "/path/to/archive_file.zip" with the actual file name of the file you've downloaded. Don't forget that file names are case sensitive in Ubuntu.

---

### Post by sudodus on 2013-01-23
I'm afraid your zip file is bad. Anyway, try with the attached zip file, which contains a simple text file
'for-help.txt'

If you can't unzip that file with the following command, there is really something wrong with ur system.

```
unzip -c for-help.zip
```

*Edit*: test a zip archive like this:
```
zip --test for-help.zip
```

---

### Post by prodigy_ on 2013-01-23
Did you change "/path/to/archive_file" to your actual path/filename? If yes, could you try **ls -l** on the archive file as a quick little sanity check?

---

### Post by Lightning Dragon on 2013-01-23
Hello,

> *I'm obviously missing something. I can't  download another unzip program like 7zip because I need to uncompress  it, but the 'archive manager' can't uncompress the program. If it did  work, I wouldn't need to download another unzip program in the first  place. Anybody know what I'm missing? Any help would be greatly  appreciated!*
The program itself is available from the Software Center or through terminal commands. Go to the Ubuntu Software Center on the side bar to the left ([or look it up in the Dash, which you can see through this link]("http://s7.postimage.org/4unbkkfmz/Screenshot_from_2013_01_23_15_18_39.png")) and search in the top right bar "7zip". You should get a screen like this;

[http://s8.postimage.org/dwzj16xid/Screenshot_from_2013_01_23_15_14_10.png](http://s8.postimage.org/dwzj16xid/Screenshot_from_2013_01_23_15_14_10.png)

Hit install and now you will be able to unzip compressed files. :)

---

### Post by brain7734 on 2013-01-23
Alright, I have successfully installed 7zip. The problem is I can't open any files with it. I try to open up a file using another program (right-click, open with...), but I can't find 7zip.

---

### Post by CharlesA on 2013-01-23
Just open 7zip and browse to the file you want to open.

Not sure why it wouldn't show in the context menu, though.

---

### Post by sudodus on 2013-01-23
The 7z commands corresponding to the zip commands in post #12 are

to extract to terminal:
```
7z -so e for-help.zip 2>/dev/null
```
and to test:
```
7z t for-help.zip
```

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Did you try rebooting after you installed 7zip? That might put it in your right click menu.

Right click the file again and click the "Open with other Application...". Now click "Show other Applications", and see if it is in the list. If it isn't, double click the file (not right click) and see if it opens up into an archive manager window now. If that doesn't work, you can now perform sudodus' suggest command line from earlier because the program has been installed.

---

### Post by brain7734 on 2013-01-23
Presto! Thanks to everybody who helped me. I appreciate all you Linux people!!

---

