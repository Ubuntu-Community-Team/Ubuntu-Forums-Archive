---
title: "downloading pictures"
date: 2015-05-03
forum: General Help
---

### Post by Camilia on 2015-05-03
I have just reinstalled ubuntu 14.10. Some pictures I save download correctly. A few don't. I probably need to download another program to view them. When I open up the picture I get message Could not load image '1.jpg'.
Error interpreting JPEG image file (Not a JPEG file: starts with 0x3c 0x21)

What program from the synapse manager will solve this problem?

---

### Post by deadflowr on 2015-05-04
Most likely the extension name is wrong.
You can remove the extension and they should be viewable with no problem.
When you remove the extension, the true format should be listed in nautilus > list view option or in the files properties.
You can also use mediainfo from the command line.

After you figure out what the actual file format is, you can add that one as the extension.

---

### Post by dino99 on 2015-05-04
'jpeginfo' is the first step to test these jpeg files (or falsely named; take care of trojan/worm/backdoor/...)

---

### Post by Stefan_Vukanovic on 2015-05-04
Also, you could try to download it with "wget <link>"

---

### Post by SeijiSensei on 2015-05-04
Use the "file" command to see if it's really as JPEG image like this:
```

$ file IMG_0661.JPG 
IMG_0661.JPG: JPEG image data, EXIF standard 2.21

```
Most likely the file is corrupt if it doesn't have the proper headers.

---

### Post by Camilia on 2015-05-04
> **deadflowr said:**
> Most likely the extension name is wrong.
You can remove the extension and they should be viewable with no problem.
When you remove the extension, the true format should be listed in nautilus > list view option or in the files properties.
You can also use mediainfo from the command line.

After you figure out what the actual file format is, you can add that one as the extension.
I deleted the extension by renaming it. Now it opens up in a web page. I prefer it to open up on the desktop so that I don't have to go on line to see the pic. That is all I understand of what you said. 

true format should be listed in nautilus > list view option or in the files properties. 
Where are those options?

You can also use mediainfo from the command line. I guess in terminal type mediainfo. That gave me no results.

> **Stefan_Vukanovic said:**
> Also, you could try to download it with "wget <link>"
How do I that? I wish when someone tells me what to do they would tell me how.

Googled nautulus  and found instruction:
To open the current directory open in Terminal, type the following command at the prompt and press Enter.
It didn't work.

Went to askubuntu.com. Asked how to download a pic with wget. Didn't find answer.

> **SeijiSensei said:**
> Use the "file" command to see if it's really as JPEG image like this:
```

$ file IMG_0661.JPG 
IMG_0661.JPG: JPEG image data, EXIF standard 2.21

```
Most likely the file is corrupt if it doesn't have the proper headers.
I guess you meant go in terminal and paste command. That gave me no results.

> **dino99 said:**
> 'jpeginfo' is the first step to test these jpeg files (or falsely named; take care of trojan/worm/backdoor/...)
I have no idea what to do with this info.

---

### Post by SeijiSensei on 2015-05-04
> **Camilia said:**
> I guess you meant go in terminal and paste command. That gave me no results.

Suppose the file is stored in /home/Camilia/Pictures and is called somepicture.jpg.  You can use the file command by opening a terminal and running the commands:
```

cd /home/Camilia/Pictures
file somepicture.jpg

```
The first command navigates to the directory where the picture is stored.  The next command runs the file command on somepicture.jpg.

The wget command works like a web browser.  You point it at a URL address, and it downloads a copy of whatever that address points to and stores it in a file.  For instance, you can get a copy of my avatar with 
```
wget 'http://www.takinganimeseriously.com/images/emperor-of-en.png'
```
I recommend getting into the habit of enclosing URLs in single quotes when using wget.  There are many special characters in URLs like the "?" and especially the "&" that will cause wget to fail if the URL is not quoted.  Single quotes tell the shell program called bash to treat a text string literally and not interpret the characters in any way.

I'm sorry if I assumed too much knowledge of the command line.  I gave you an example of how the command would be used with a file called IMG_0661.JPG on my own machine.  I didn't think you might interpret that literally and type the same thing.  My fault.

---

### Post by Camilia on 2015-05-04
> **SeijiSensei said:**
> Suppose the file is stored in /home/Camilia/Pictures and is called somepicture.jpg.  You can use the file command by opening a terminal and running the commands:
```

cd /home/Camilia/Pictures
file somepicture.jpg

```

Well doing that with no extension didn't work so downloaded the pic again. This time before saving it clicked on all files. It saved as it was suppose to. LOL

---

### Post by SeijiSensei on 2015-05-04
> **Camilia said:**
> Well doing that with no extension didn't work
The reason I suggested using the file command is that it doesn't care about extensions at all.  It looks at the contents of the file, particularly its "headers," to determine the type of file it is.  You can see that by deleting the extension off a picture and running file against it.  It will still tell you the correct type.  For instance,
```

mv emperor-of-en.png emperor-of-en
file emperor-of-en 
emperor-of-en: PNG image data, 90 x 90, 8-bit/color RGBA, non-interlaced
```

---

### Post by Camilia on 2015-05-04
In terminal pasted cd: /home/Camilia/Pictures: No such file or directory
kim@brain:~$ file needle setup.jpg
needle:    cannot open `needle' (No such file or directory)
setup.jpg: cannot open `setup.jpg' (No such file or directory)
So understand what I suppose to do in the terminal. Doesn't matter. Problem solved.

---

### Post by SeijiSensei on 2015-05-04
> **Camilia said:**
> In terminal pasted cd: /home/Camilia/Pictures: No such file or directory

I don't know what your Ubuntu username is, Camilia, so I used the one here.  I also have no idea where the picture is stored on your computer so I used the standard Ubuntu "Pictures" directory instead.  You need to know the directory where the picture is stored, then use the command "cd /path/to/that/directory" replacing "/path/to/that/directory" with the complete path to the directory holding the picture.

Rather than literally copying and pasting terminal commands, stop and think a bit about what they are supposed to be illustrating.  An example like
```

sudo apt-get update
sudo apt-get install gimp

```
to install the GIMP image editor has no possible customizations.  But a command that requires knowing about specific features of your own computer like the location of downloaded files can only be given through illustration with an example.  In those cases you need to adapt the example to your own specific circumstances.

---

