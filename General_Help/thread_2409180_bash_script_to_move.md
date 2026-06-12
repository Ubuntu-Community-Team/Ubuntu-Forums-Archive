---
title: "bash script to move"
date: 2018-12-28
forum: General Help
---

### Post by sickpig24 on 2018-12-28
hi All

in windows i had created a simple bat file to move files in my download to other folders based on their extensions

trying to do the same in bash script but it does not like wild characters it seems(its more likely i dont know what i am doing). i have read similar posts about moving files based on their entensions via bash script but those posts did not have clear examples.

Any help appreciated
thanks.

---

### Post by HermanAB on 2018-12-29
A few pointers:
As you found, wild cards in Bash are not exactly the same as in Windows.
For example: '*' includes '.' and '..' means: The previous directory. So if you use '.*', then your script will traverse the whole file system, up and down the tree.
Recursion, to search directory trees, is best handled with the 'find' command, using the 'exec' option.
A space in UNIX, is a delimiter (a break indicating the start of the next command option).  Therefore, strings have to be quoted, if they could include spaces.
Single quotes do exactly what is written on the tin.  Double quotes, will do the same AND expand $variables.

'Hope that helps!

---

### Post by CatKiller on 2018-12-29
The term you're looking for is **regular expressions**. You should be able to find plenty of examples knowing the name of them.

---

### Post by sickpig24 on 2018-12-29
Thanks for replies guys

i have tried below

mv /home/downloads/*.png /home/images


mv ~/home/downloads/*{.png} ~/home/images


mv /home/downloads/*+(.png) /home/images

the first one ofcouse wont work as we know, not sure about the other two

can someone post an example of a simple move command for moving  files  based on their extensions please.

I am not being lazy and just asking for a handout. I have tried googling and creating one but its not working.

appreciate  any help
thanks.

---

### Post by spjackson on 2018-12-29
> **sickpig24 said:**
> 
i have tried below

mv /home/downloads/*.png /home/images


In terms of wildcard usage the above would be what you want. The problem is almost certainly the directory specification. The directories /home/downloads and /home/images are very unlikely to exist. Note also that Linux filesystems are case sensitive. What you probably want is:
```

mv ~/Downloads/*.png ~/images

```
or possibly
```

mv ~/Downloads/*.png ~/Images

```
The downloads folder normally begins with an uppercase D, although it could be changed.

---

### Post by sickpig24 on 2018-12-30
thank u  for making my life easier Sir
the home was just some name i used in place of my home folder
you were spot on about the download folder being case sensetive
changing it made the magic happen
thanks a bunch
i will go on my merry way now to add all the little tweaks and mods to replicate my windows setup

appreciate you taking the time in helping me
cheers

---

### Post by vidtek on 2018-12-30
Sickpig-

Don't forget to mark this as solved.  It helps others searching for solutions to similar issues.

Cheers, Tony.

---

### Post by HermanAB on 2018-12-30
Err.. as alluded to above, don't put a '*' and a '.' next to each other in a path, since one of the permutations result in '..' which means the previous (lower) directory, which is usually not wanted, since it will cause the script to traverse a much larger swath of the file system than any sane person would expect.

So, instead of '*.png', only use '*png'.

---

### Post by Impavidus on 2018-12-30
*. is fine, at least in the normal bash shell. It won't expand to anything stating with . . The thing you usually want to avoid is .*, which will expand to every file and directory starting with ., including .., which can make it traverse the entire directory tree.

---

### Post by CatKiller on 2018-12-30
Coming back to this one, it's *almost* something that would be quite useful. 
> **sickpig24 said:**
> 
mv ~/home/downloads/*{.png} ~/home/images
You can use the curly brackets to define a set. So, knowing that, you can probably work out what this does:
```
mv ~/Downloads/{*.png,*.PNG,*.jpg,*.JPG,*.bmp,*.BMP} ~/Images/
```

There's more information on wildcards and regular expressions [here](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm).

---

### Post by sickpig24 on 2018-12-30
whoa blown away by the wealth of information here
thanks heaps to all
off topic - am enjoying my new linux distro. it runs off ram and is so unbelivably fast. makes me wonder why did i not think of this earlier. i feel i have just stopped being a cave man.
i have managed to get netflix going, setup dropbox, get my move script going. thats it i think i can use it as primary os now. did i say how fast it is. 
ok now will figure out how to mark this as solved.

---

