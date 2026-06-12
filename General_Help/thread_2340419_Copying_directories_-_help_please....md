---
title: "Copying directories - help please..."
date: 2016-10-18
forum: General Help
---

### Post by pat4 on 2016-10-18
I have  a three sub-directories in my home/documents directory that I wish to back up (i.e., copy) to two different hard drives.   The relevant directories are named BC  BD and BG.

The hard drives are internal to my machine and are mounted at /media/pat/Disc5  and  /media/pat/Disc6  respectively. 

My question is a two parter... 

1.  Is it possible to copy all three directories (and enclosed files) to one hard drive using one command rather than doing each directory separately?  If so, some help with the syntax of the command would be helpful.

2. Is it further possible to copy all three directories to both backup drives simultaneously, using one command?

Any and all help appreciated.

Thank you.

Pat.

---

### Post by Habitual on 2016-10-18
duplicates?

---

### Post by Impavidus on 2016-10-18
1: Use cp:```
cp -r source1 source2 source3 destination
```
2: Use tar to pack the directories into a single stream and pipe it to two destinations:```
tar -cf - source1 source2 source3 | tee >(tar -xf - -C destination1) | tar -xf - -C destination2
```

---

### Post by untrustytahr on 2016-10-18
1. ```
cp -rt /media/pat/Disc5 Documents/B{C,D,G}
```

2. cp doesn't have a multi-dest option so you would have to do a loop:
```

for i in /media/pat/Disc{5,6}; do cp -r Documents/B{C,D,G} $i; done
```

---

### Post by pat4 on 2016-10-18
Thank you all for your responses.. 
To Habitual, duplicates are not an issue...
Impavidus - I will add using Tar to my learning curve.  
untrustytahr - likewise, using a loop is something I need to research. 

I appreciate your help. 

Kind regards,   Pat.

---

### Post by Impavidus on 2016-10-19
> **pat4 said:**
> Impavidus - I will add using Tar to my learning curve.
Tar was not the most interesting part of that command. I only used it to pack entire directories into a single file and write it to standard output, then read standard input and unpack those directories. That is necessary to work with directories, as the stuff in the middle only works on single files. And to conserve permissions.

The interesting part are the pipes (the | syntax), tee and process substitution (the >(foo) syntax).

The directories, packed into one stream by the first tar, are first piped into tee. Tee duplicates the stream and forwards it via the second pipe to the last tar, which unpacks the stuff into destination2. The shell handles the process substitution by creating a temporary named pipe and connecting it to standard input of the middle tar command. The shell puts the name of the pipe on the command line of tee. Tee forwards its input also to the file named on its command line, thus piping it to the middle tar command, which in turn unpacks it into destination1. So you get two tar processes, each unpacking exactly that which is packed by the first tar command, but in two different directories.

If you want to learn the command line in Linux, you have to learn about pipes.

The loop mentioned by untrustytahr works too, but will read the directories to be copied twice. With modern disk read caching, it shouldn't matter too much.

Command line help (brief mention of pipes): [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)
Wikipedia on pipes: [https://en.wikipedia.org/wiki/Anonymous_pipe](https://en.wikipedia.org/wiki/Anonymous_pipe)
Wikipedia on process substitution: [https://en.wikipedia.org/wiki/Process_substitution](https://en.wikipedia.org/wiki/Process_substitution)

---

### Post by HermanAB on 2016-10-19
rsync is a better kind of cp

---

### Post by pat4 on 2016-10-20
Thanks once again for your responses...
I clearly have a lot to learn and will follow up on the links helpfully provided by Impavidus.   Rsync is also something else I need to look into - thanks HermanAB...

Alexeyn - sorry I don't understand your comment...

Kind regards,  Pat.

---

### Post by kjohri on 2016-10-21
cd ~/documents
for i in 5 6
do
sudo rsync -avz BC BD BG /media/pat/Dics${i}
done

For bulk copying of files, rsync is a better option.

[https://www.softprayog.in/tutorials/rsync]("https://www.softprayog.in/tutorials/rsync")

---

