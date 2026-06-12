---
title: "Using Terminal to list files in subdirectories in alphabetical order"
date: 2008-03-06
forum: General Help
---

### Post by bobbo85 on 2008-03-06
I am trying to delete duplicate mp3 files that are in different subdirectories.  My first idea was to use the ls command like this:
ls -R

But this is not listed in alphabetical order, and it includes all of the folder names too.  

The next idea was to try 
ls -R *.mp3
ls: *.mp3: No such file or directory

In fact, anything other than ls -R * gives me the same response.

My next idea was to try
ls -R |grep mp3

This listed the mp3s without folders, but still not in alphabetical order.

So the question is... how can I get this list in order?

---

### Post by Het Irv on 2008-03-06
I think if you just type ```
ls
``` while you are in the directory, it is in alpha order by coulmn (down then across).

---

### Post by bobbo85 on 2008-03-06
> **Het Irv said:**
> I think if you just type ```
ls
``` while you are in the directory, it is in alpha order by coulmn (down then across).

Thanks for the quick response Het.

Yeah I noticed ls sorts alphabetically by default, but it seems that using -R (recursive) to list files in subfolders is screwing things up.  

1)  The sort is being done on the directories, not the files within them.
2)  Adding any search words makes it fail (I can't search for anything other than * )

---

### Post by YoG%*@ on 2008-03-06
hi,

you could 
```
ls -R | grep mp3 | sort 
``` 

but maybe someone else knows of a better / more elegant solution..?

hth,
mux

---

### Post by Het Irv on 2008-03-06
Here is the page that I am using.  I am just trying different combos of the options.

BTW:[COLOR="SeaGreen"] Het Irv or Irv[/COLOR], not [COLOR="Red"]Het[/COLOR]

Edit: or you could listen to the guy above, that worked for me somewhat (it did not return any files that had track numbers in front, 
e.g. 01-Attack.mp3 was not found, but pfk_14.mp3 was)

---

### Post by bobbo85 on 2008-03-06
> **Het Irv said:**
> Here is the page that I am using.  I am just trying different combos of the options.

BTW:[COLOR="SeaGreen"] Het Irv or Irv[/COLOR], not [COLOR="Red"]Het[/COLOR]

Edit: or you could listen to the guy above, that worked for me somewhat (it did not return any files that had track numbers in front, 
e.g. 01-Attack.mp3 was not found, but pfk_14.mp3 was)

What page?

Yeah, I got ls -R | grep mp3 | sort
to list the files... however, there are no directories.

I just tried using 
find -name *.mp3

Which lists all of the files, plus their directories...  so can I get this to sort by filename and not directory?

I suppose at this point I could use the ls command to look for identical filenames, then use the find command to search for that filename, which would show me the directories the file is in, and i could then rm one of the two copies...

That seems to be entirely too much work though!

---

### Post by Het Irv on 2008-03-06
Sorry, I forgot to tell you I was sending it Telepathically.  
[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=l/ls]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=l/ls")
[URL="http://www.linuxdevcenter.com/linux/cmd/"]
http://www.linuxdevcenter.com/linux/cmd/[/URL]  Here is the Homepage that list all commands and their options.

---

### Post by bodhi.zazen on 2008-03-06
```
find . -name "*.mp3"
```

From there you can manipulate the list.

find is very powerful and will do so much more ...

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by bobbo85 on 2008-03-06
> **bodhi.zazen said:**
> ```
find . -name "*.mp3"
```

From there you can manipulate the list.

find is very powerful and will do so much more ...

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)


Thank you, but I was still unable to find any references to sorting options...  

As far as I understand it, find will get me a list of all the files, using their full file names (including directory)
LS will get me a list of all the files, without their locations.

And piping either command to sort only sorts the string passed to it character by character - meaning the part of the string that is the location is sorted first, because it is before the part of the string that contains the filename. 

I'm just looking for a way to sort files by filename, and list them by their full names (including their location!)

---

### Post by bodhi.zazen on 2008-03-06
What do you want the output to look like ?

```
for i in `find . -name "*.mp3"`; do echo ""${i##*/}" "$i""  >> list; done; column -t list | sort | grep .mp3 >> mp3_files; rm list
```

Will give you 

name.mp3     /full/path

sorted in a file "mp3_files"

I added the grep (when testing on .txt files found some non- *.txt :( )

---

### Post by bobbo85 on 2008-03-06
> **bodhi.zazen said:**
> What do you want the output to look like ?

```
for i in `find . -name "*.mp3"`; do echo ""${i##*/}" "$i""  >> list; done; column -t list | sort | grep .mp3 >> mp3_files; rm list
```

Will give you 

name.mp3     /full/path

sorted in a file "mp3_files"

I added the grep (when testing on .txt files found some non- *.txt :( )


Here's the command I ran (from home directory):
```
for i in `find "/media/BOBBY'S IPO" -name "*.mp3"`; do echo ""${i##*/}" "$i""  | sort >> list; column list >> mp3_files; done; rm list
```

Here's the output I got (the file mp3_files is a 5.7mb file so i just took out a sample of the pattern):

BOBBY'S /media/BOBBY'S
Dispatch IPO/iPod_Control/Music/f73/Dispatch
- -
04 04
Flying Flying
Horses.mp3 Horses.mp3
BOBBY'S /media/BOBBY'S
03 IPO/iPod_Control/Music/f73/03
Today.mp3 Today.mp3

---

### Post by ryanhaigh on 2008-03-06
```
sudo apt-get install fdupes
cd /base/music/dir/
fdupes ./ -r

```

I know it isn't answering your bash question but this will find all duplicate files and optionally delete them using the -d or option. I did a similar thing with images as per [this post]("http://ubuntuforums.org/showthread.php?p=4400446#post4400456") but I copied all files to one folder first so didn't need the -r option.

You may not want to use the keypressing thing if you want to choose which files to keep but fdupes will do what you want using the file data rather than the name to find duplicates.

---

### Post by bodhi.zazen on 2008-03-06
> **bobbo85 said:**
> Here's the command I ran (from home directory) <clip>

Sorry, I edited that command.

Try it again :

```
for i in `find . -name "*.mp3"`; do echo ""${i##*/}" "$i""  >> list; done; column -t list | sort | grep .mp3 >> mp3_files; rm list
```

---

### Post by bodhi.zazen on 2008-03-06
> **ryanhaigh said:**
> ```
sudo apt-get install fdupes
cd /base/music/dir/
fdupes ./ -r

```

I know it isn't answering your bash question but this will find all duplicate files and optionally delete them using the -d or option. I did a similar thing with images as per [this post]("http://ubuntuforums.org/showthread.php?p=4400446#post4400456") but I copied all files to one folder first so didn't need the -r option.

You may not want to use the keypressing thing if you want to choose which files to keep but fdupes will do what you want using the file data rather than the name to find duplicates.

Nice post, thanks for the info.

You need to use caution re: automated deletion of duplicates ... but you could use yes :

```
yes 1 | fdupes -r -d
```

The problem with that approach is you can obviously delete the wrong file :(

(fdupes **uses the md5sum rather then the file name** to identify duplicate files and you need to be very careful with empty files)

/bodhi.zazen adds fdupes to the armormentarium

---

### Post by ryanhaigh on 2008-03-06
> **bodhi.zazen said:**
> 
You need to use caution re: automated deletion of duplicates ... but you could use yes :

```
yes 1 | fdupes -r -d
```

(fdupes **uses the md5sum rather then the file name** to identify duplicate files and you need to be very careful with empty files)

You are welcome and thanks in return for the yes thing will be very useful. Same again for the empty file warning, although not relevant for anything i have done YET, good to keep in mind.

---

### Post by kuja on 2008-03-12
Saw this post a few days ago and remembered it earlier this morning, and seeing as I had some cleaning up to do myself I whipped something together. Not sure if it will be useful at this point but oh well. 

I've attatched my solution: a small python script. It requires the setting of 3 variables at the top of the file.

---

