---
title: "Creating new file + renaming it immediately"
date: 2022-06-20
forum: General Help
---

### Post by bgway on 2022-06-20
I added the option to create new file by right-clicking after adding a text file to the Templates folder:

```
[FONT=var(--theme-post-body-font-family)]touch ~/Templates/Untitled.txt[/FONT]
```[FONT=inherit][FONT=inherit][COLOR=#232629][FONT=-apple-system][FONT=inherit]
[/FONT]
[/FONT][/COLOR][/FONT][/FONT]
But, it creates a text file with the name provided. Is it possible to create a new file, and then immediately after you create it, make it already in the renaming session? Just like when you right-click and create a new file on Window

---

### Post by coley9225 on 2022-06-20
I don't see a reason to use templates with basic text file(file.txt). I usually right click in folder from file manager and select new file, name the file, then open and type the contents of the file. If your making a file from a text editor, simply save as file name and choose your location to save to. If you have a non-standard use case, where a template is needed, and you creating a 'template' for future use, then same as stated, and save to template directory(folder).

A little more details on what it is your trying to do would help. If your running the command from terminal, just name the file at that time rather trying to make a "generic" file name and then renaming. If your doing this from a script, then modify to allow you to enter a file name prior to making the file.

Without more info on what your process is intended to do, I really have nothing else to offer. Possibly you give an example of the end goal, and the path your taking, maybe then someone can offer a better way to get to the end result.

---

### Post by vanadium on 2022-06-21
I answered to this question on [Askubuntu](https://askubuntu.com/a/1415051/558158). I never missed such feature - I find it easy enough to hit F2 to rename the new file.

---

### Post by mIk3_08 on 2022-06-22
> **bgway said:**
> I added the option to create new file by right-clicking after adding a text file to the Templates folder:
```
[FONT=var(--theme-post-body-font-family)]touch ~/Templates/Untitled.txt[/FONT]
```
But, it creates a text file with the name provided. Is it possible to create a new file, and then immediately after you create it, make it already in the renaming session? Just like when you right-click and create a new file on Window
To rename file we just use mv command example below;
```
sudo mv '/homedirectory/myusername/Documents/filename-to-be-rename' '/homedirectory/myusername/Documents/to-be-the-final-name'
```
Regards and cheers

---

### Post by HermanAB on 2022-06-22
Why don’t you create the file with the correct name to begin with?

You could make an interactive script that will ask for the filename with Zenity dialogue boxes.  Here is some information: https://www.aeronetworks.ca/2015/09/?m=1

---

### Post by mIk3_08 on 2022-06-23
> **bgway said:**
> I added the option to create new file by right-clicking after adding a text file to the Templates folder:
But, it creates a text file with the name provided. Is it possible to create a new file, and then immediately after you create it, make it already in the renaming session? Just like when you right-click and create a new file on Window
> **HermanAB said:**
> Why don’t you create the file with the correct name to begin with?
I agree with HermanAB... Why waste time for renaming while you can create directly a finale filename for each file. Regards and cheers

---

