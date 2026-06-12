---
title: "Archive type not supported in ubuntu 16.04"
date: 2016-07-20
forum: General Help
---

### Post by mountainman70 on 2016-07-20
Since an update I have been unable to open any of my text files. Every file says " Could not open ____." Archive type not supported.
Have tried other text editors and get the same results.

---

### Post by &amp;KyT$0P# on 2016-07-20
What update, what kind of update?
Are these text files inside archives or just normally stored on the file system?
Specifically what text editors are you trying?

Can you please open a Terminal, run these commands on an affected text file, and post here their output?
```
file -b <one of the affected text files>
file -b -i <one of the affected text files>
```

---

### Post by mountainman70 on 2016-07-20
> **halogen2 said:**
> What update, what kind of update?
Are these text files inside archives or just normally stored on the file system?
Specifically what text editors are you trying?

Can you please open a Terminal, run these commands on an affected text file, and post here their output?
```
file -b <one of the affected text files>
file -b -i <one of the affected text files>
```

blank-OptiPlex-960:~$ file -b Michael McGarrity.txt
cannot open `Michael' (No such file or directory)
cannot open `McGarrity' (No such file or directory)
cannot open `.txt' (No such file or directory)
blank-OptiPlex-960:~$ file -b -i Michael McGarrity.txt
cannot open `Michael' (No such file or directory)
cannot open `McGarrity' (No such file or directory)
cannot open `.txt' (No such file or directory)

I have upgraded from 14.04 LTS to 16.04 LTS and everything was working fine. i could open any text file from a URL to a web site to my text file for my medicine that I keep updated. Gedit would not work in 16.04 but pluma would. On some files like the file above, pluma would open a screen that said it was an executable text file and give me the option to "run in terminal", "display", "cancel" or "run". The file above is just a list of books by that author. Tried other text editors and they show Archive type not supported.
There have been at least two updates to 16.04 since I noticed this problem today.

---

### Post by mountainman70 on 2016-07-20
OK. I have solved my problem. I opened a file with "Open with" chose "Other Application" and scrolled to Leafpad and checked "remember this application for plain text documents file". All files now open in Leafpad. So simple when I remembered what to do. 
Thanks for the reply.

---

### Post by vasa1 on 2016-07-20
> **mountainman70 said:**
> OK. I have solved my problem. ...
That's nice. But you may want to get into the habit of _not_ having spaces in filenames.

Here's a link that you may like to look at: [Filenames: What's In A Name?]("http://pclosmag.com/html/Issues/201607/page03.html") especially the section titled "Making safe choices".

---

