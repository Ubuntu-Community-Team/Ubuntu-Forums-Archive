---
title: "Mass File Rename"
date: 2005-07-13
forum: General Help
---

### Post by Leav on 2005-07-13
Using "Motion" I have captured about 800 pictures from my webcam.
I would like to try and convert them to an mpeg movie.

I will be using mjpeg, but for that i need to rename the files.

example of file name:

06-20050713220646-00.jpg

I would like to try this script to rename all the files in the directory to correct name format for mjpeg:
```

count=0
for item in `ls -t *.jpg`
do 
  mv $item frame-`printf "%05d" $count`.jpg
  count=$(( $count + 1 ))
done

```

'ls -t *.jpeg' is supposed to find all jpeg files and sort them by date.
everything else should be obvious......

my questions:
1)will this work?
2)I can't run this? what should i do? i tried going to the directory from the command line and typing ```
sudo ./rename_jpeg.sh
``` but that just returns command not found.... any ideas?

Thanks!
-Leav

---

### Post by varunus on 2005-07-13
Did you make the script executable?  (ls -l should show "x" for the file.)  Try "chmod +x thescriptname.sh" and then running it.

Good luck.

---

### Post by Leav on 2005-07-13
[QUOTE=varunus]Did you make the script executable?  (ls -l should show "x" for the file.)  Try "chmod +x thescriptname.sh" and then running it.

Good luck.[/QUOTE]
 Thanks Varunus, that helped a bit, now i can run the file! :)

now i get:
```

leav@leavsbox:/var/www/cam1$ sudo ./rename_jpeg.sh
./rename_jpeg.sh: line 4: unexpected EOF while looking for matching ``'
./rename_jpeg.sh: line 7: syntax error: unexpected end of file

```

line 4 is this:
```
 mv $item frame-`printf "%05d" $count`.jpg
```

and line 7 is non-existant (i.e. the line is blank on the file and there is nothing after it).

would you mind helping me out?

Thanks again!
-Leav

---

### Post by poptones on 2005-07-13
Did you get it yet?

Try this:

```
count=1000000
for item in `ls -1 -t *.jpg`
do 
  mv $item frame-${count:1}.jpg
  let "count=$count + 1"
done

```

Keep in mind that, if there are any spaces in your filenames, the 'for" will screw up the works completely because "my downloads" is two $items.

---

### Post by wylfing on 2005-07-13
Closer.

@Leav - You need to get rid of the double quotes around %05d. They're not needed to make printf work.

@poptones - 'ls -t' is sufficient, he doesn't need -l in there too. I like the 'let' but I still think 'printf' was the right idea. I don't see a need to fear spaces in filenames given the original example, but that can be overcome with double quotes.

I also **strongly recommend** using 'cp' instead of 'mv' in a script of this nature. You can always easily clean up the original files later, but you can't go back if you screw up the 'mv' somehow (e.g., suppose $count doesn't get incremented, you'll lose all your data).

That said, I think this is how to fix your script:
```
#!/bin/bash

count=0
for item in `ls -t *.jpg`
do
  cp "$item" frame-`printf %05d $count`.jpg
  let "count+=1"
done

```

---

### Post by ubuntp on 2005-07-13
You can also try this: [http://mathrick.org/software/purrr.html](http://mathrick.org/software/purrr.html)

---

### Post by wylfing on 2005-07-13
Oh, sure, but you don't get any shell hacker cool points  ;-)

---

### Post by ubuntp on 2005-07-13
That's the spirit! ;)

---

### Post by poptones on 2005-07-14
>  'ls -t' is sufficient, he doesn't need -l in there too.

It's a 1. As in "-w1" but without the w cuz I'm 2 lazy 2 type it.

> I like the 'let' but I still think 'printf' was the right idea.

Actually I just ripped most of it off my command line history. I often work with large video sequences and I use a 6 digit counter. But I'd still like to know why printf is preferable here. Keep in mind I am not a c guru and I hate perl and anything that remotely resembles it :) 

>  I don't see a need to fear spaces in filenames given the original example, but that can be overcome with double quotes.

Perhaps you could illustrate something that works in a FOR loop with spaces in the filenames? I've never seen a solution that works and all the online help I find on bash says to use while... so I do.

---

### Post by Leav on 2005-07-14
[QUOTE=poptones]It's a 1. As in "-w1" but without the w cuz I'm 2 lazy 2 type it.



Actually I just ripped most of it off my command line history. I often work with large video sequences and I use a 6 digit counter. But I'd still like to know why printf is preferable here. Keep in mind I am not a c guru and I hate perl and anything that remotely resembles it :) 



Perhaps you could illustrate something that works in a FOR loop with spaces in the filenames? I've never seen a solution that works and all the online help I find on bash says to use while... so I do.[/QUOTE]
 Thanks alot everyone, the script works great! (both of them :) )

some questions though:
-what does the command "mv" do? move? as in "cut & paste"+rename?

-**poptones**, why did you use "count=1000000" at the start and why "count:1" when using that for a file name?

-is /bin/bash/ the place to put scripts?

-where can i learn more (maybe a tutorial) about linux (ubuntu?) scripting?

Thanks ALOT!, 
-Leav

---

### Post by poptones on 2005-07-14
The "count=1000000" is a cheap hack. It's an easy way to make sure you have a fully padded number for proper indexing. When you echo a variable the : sets the position in the string. Example: if foo=123456 then ${foo:0:3} is 123 and ${foo:3} is 456. 

Get it? So ${count:1} is just 1000000 without the leading 1. If you try a for loop or the seq operator it doesn't pad the same way. There are many ways to skin that cat, I just use this one because I find it most readable.

mv is move. cp is copy. If you do not delete the files form your camera and something goes wrong you're still OK, but if you use mv on the only copy of a file and it screws up, you're had and that's that. The difference here (and one I experience a lot myself because, as I said, I also do video and it makes a LOT of difference when you're dealing wiht tens of thousands of frames) is that a "mv" just overwrites a pointer to the file and cp requires copying the entire file to a new position. the difference in time between "cp" 1000 files vs "mv" 1000 files could be several minutes - enough time to justify the risk so long as you are not working with the ONLY existing copy of your data.

---

### Post by yanik on 2005-07-14
> where can i learn more (maybe a tutorial) about linux (ubuntu?) scripting?

here [http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)
then [http://www.tldp.org/LDP/abs/abs-guide.pdf](http://www.tldp.org/LDP/abs/abs-guide.pdf)

Bash scripting is the same on all linux distro.

---

### Post by wylfing on 2005-07-15
[QUOTE=poptones]It's a 1. As in "-w1" but without the w cuz I'm 2 lazy 2 type it.[/QUOTE]
Oops! My face is red.

[QUOTE=poptones]But I'd still like to know why printf is preferable here.[/QUOTE]
Er, well...I feel like it's self-documenting that way. There are quite a lot of people who can look at a printf statement and know exactly what's happening, so if anyone needed to help with this script in the future they'd have an easy time of it. I think fewer people would understand the "hack" (as you called it) of pushing the end off a string of numbers.

[QUOTE=poptones]Perhaps you could illustrate something that works in a FOR loop with spaces in the filenames?[/QUOTE]
It's really easy. The way 'ls' was used in the script we've been discussing was actually unnecessary. You can just tell bash to look at wildcards directly. For example:
```
for file in *.jpg
do
    cp "$file" "$file"~
done
```
This would back up all files ending in .jpg by making a copy with ~ at the end (typical Unix-y way to do things). Spaces in the file name would be no problem because of the double quotes around the variable.

HTH

---

