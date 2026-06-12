---
title: "How to change file type"
date: 2015-01-09
forum: General Help
---

### Post by fkervin on 2015-01-09
Hi all,

I'm having some problems with a few of graphic files (png), the problem is the system doesn't recognize them correctly.

I've try to run "ls" from terminal in the folder they're stored and in the list, while some files appears in pink color (what means image file if i'm not wrong), other ones appears in green color (executable or recognized data file).

How can I change the file type to image, in other words, how can I change those files from green to pink?. I know using "chmod +x" a file can be made executable, but... how to convert into "image file" and make it appear pink?

Many thanks in advance

---

### Post by Frogs Hair on 2015-01-09
I have used gimp from the software center in the past . Open with gimp and then use export as and this has corrected errors I've experienced with some images. Renaming sometimes works as well.

> [COLOR=#000000]how to convert into "image file" and make it appear pink?[/COLOR]

I'm not sure what you mean by pink.

---

### Post by Yellow Pasque on 2015-01-09
If it really is a PNG file, "chmod -x <filename> will change it from green to pink.
file command is useful here too:
```
file <filename>
```


> I'm not sure what you mean by pink. 
Video and picture files are listed in pink in bash.

---

### Post by vasa1 on 2015-01-09
> **Frogs Hair said:**
> ...
I'm not sure what you mean by pink.
When you list files in the terminal, the font colors of files, by default, are different depending on whether they're directories, text files, images, logical links etc. Even on my system, image files are "pink".

Also: [http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal](http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal)

---

### Post by mc4man on 2015-01-09
> **Temüjin said:**
> If it really is a PNG file, "chmod -x <filename> will change it from green to pink.

likely the case here, for some reason some png's are marked executable. Has happened here on rare occasion with some .mp4's, no real idea why.
(may have been related to coping, storing, bringing back method or who knows...

They could refresh the db that ends up in the dircolors binary as it's missing some now common mimes but probably not on anyones do to list.

---

### Post by fkervin on 2015-01-10
Many thanks to all for the answer :D

In the past I've had similar problems to this and I've solve it using the trick of copying those files to an USB drive formatted with FAT32 format and once copied here, moving them to the location I need. It seems that FAT32 format doesn't support the features needed to "store" the file type so all them are reset.

The thing is I want lo learn why does this problem really happend and solve it correctly. I've try to make "chown -x filename.png" and it changes from green to pink, then I've try "chmod -x ." to make it to all the files in the folder, but instead of converting all files "to pink" they dissapear to "ls" command and I only can see them using "sudo ls", but they appears white (no colour), if then I make "sudo chmod +x ." they back to the "default color" (green the ones that was green and pink the ones that was pink).

¿How can I make a "chmod -x" to all the files?

Many thanks in advance :)

---

### Post by steeldriver on 2015-01-10
The command

```

chmod -x .

```

removes execute permission from the current directory "." and since directories use execute permission to indicate whether a user is allowed to open them, that stops the 'ls' command from being able to see inside. Instead, you should use a file glob (wildcard)

```

chmod -x *.png

```

or (if you need the change to be applied recursively to ALL png files, including those in subdirectories)

```

find -type f -name '*.png' -exec chmod -x {} +

```

---

### Post by Impavidus on 2015-01-10
The colours used by ls depend on:
- Type, as in ordinary file, directory, symbolic link and many more exotic types, and in case of a symbolic link whether it's valid or not.
- Permissions, like execute permissions, set user ID bit and some others.
- File type, as guessed from the file extension (if there is any)

Usb sticks usually don't support permissions, so when copying something to an usb stick and back, the permissions will be reset. The execute bit, which caused the green colour, will go away and .png files will turn magenta again. The chmod command can also remove the execute permission.

If you wish, you can easily change the rules determining the colours. Run ```
dircolors -p >dircolour-template
``` to generate a template for your colour definitions. Edit the file **dircolour-template** to get something you like and safe it. Then run ```
dircolors -b dircolour-template
```and append the output to your **.bashrc** file. The next time you open a terminal you'll get the new colours.

---

