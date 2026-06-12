---
title: "Bulk renamer Nemo space error"
date: 2016-09-06
forum: General Help
---

### Post by zuto2 on 2016-09-06
I use Thunar bulk renamer on Ubuntu and Nemo file manager. If the files have any spaces, then the Nemo file manager command does not work. At least for launching it by selecting files. I can always launch, select, drag, and drop my files.
```

thunar --bulk-rename %F
```

```
thunar --bulk-rename
```

Any ideas on a fix or will underscore be my new bestfriend? Do I have to dump Miss Space?

---

### Post by mook765 on 2016-09-06
Lost in Space...
You should avoid using spaces in file-names. Files without spaces in their name are just easier to handle.
Indeed it is allowed to have spaces in a file-name.
For a file which is named "This is my file" you would have to use
```
This\ is\ my\ file
'This is my file'
```
Both variants are possible.
But better to name the file "This_is_my_file."
This will avoid confusion when you want to use commands in terminal.

---

### Post by sampayu on 2016-10-01
> **zuto2 said:**
> I use Thunar bulk renamer on Ubuntu and Nemo file manager. If the files have any spaces, then the Nemo file manager command does not work. At least for launching it by selecting files. I can always launch, select, drag, and drop my files.
```

thunar --bulk-rename %F
```

```
thunar --bulk-rename
```

Any ideas on a fix or will underscore be my new bestfriend? Do I have to dump Miss Space?

I use XUbuntu (Ubuntu with Xfce GUI, which comes with Thunar as its default file manager). When I want to start Thunar's bulk renamer from the shell terminal, I just execute this command:

```
thunar -B /path/to/parent/folder/*
```

For instance, if under **/home/myusername/Music/Antonio Vivaldi - Cello Concertos/** I keep these five MP3 files:

[B]01 - Antonio Vivaldi - Concerto in Gmajo (G-Dur) RV415 1 Allegro.mp3
02 - Antonio Vivaldi - Concerto In Gmajo (G-Dur) RV415 11 Siciliana.mp3
03 - Antonio Vivaldi - Concerto In Gmajo (G-Dur) RV415 111 Alla Breve.mp3
04 - Antonio Vivaldi - Concerto In A Minor (A-Moll) RV420 1 Andante.mp3
05 - Antonio Vivaldi - Concerto In A Minor (A-Moll) RV420 11 Adagio.mp3[/B] 

...and at the shell terminal I wish to start Thunar's bulk renamer for these files, I simply execute this command:

```
thunar -B ~/Music/Antonio Vivaldi - Cello Concertos/*
```

...which causes Thunar to start the bulk renamer at **~/Music/Antonio Vivaldi - Cello Concertos/** and show **all files** inside of **~/Music/Antonio Vivaldi - Cello Concertos/**

Now let's assume that inside that folder there are also other MP3 files and their names begin with 06, 07, 08, 09, 10, 11, 12, 13 and 14. Let's also assume that other file names inside that folder begin with **1** but their extensions aren't ".mp3", and let's finally assume that one wants to bulk rename only **MP3** files whose names begin with 10, 11, 12, 13 or 14. In such case, one can execute this command:

```
thunar -B ~/Music/Antonio Vivaldi - Cello Concertos/1*.mp3
```

...which causes Thunar to start the bulk renamer at **~/Music/Antonio Vivaldi - Cello Concertos/** and show **all _MP3_ files** inside of **~/Music/Antonio Vivaldi - Cello Concertos/** whose names begin with **1**

_Footnotes_:

[LIST]
[*]The asterisk character ( ***** ) is a wildcard: at the above example, it means "all files". 
[*]The tilde character ( **~** ) is a wildcard, too: it means "the path to the home folder of the currently connected user". So if your username is **myusername** and your home folder is **/home/myusername** and you're currently connected to your Linux system as user **myusername**, then the command **cd ~** will produce the same result as the command **cd /home/myusername**, and **ls -l ~** will do the same as **ls -l /home/myusername**, and so on... 
[/LIST]

---

