---
title: "how to install &quot;.install&quot; file?"
date: 2020-07-06
forum: General Help
---

### Post by richmilnix on 2020-07-06
tl;dr = novice user has a file called "raisedr.install" and doesn't know how to install the program.

------------------------------

A year ago, both SATA HDDs in my Buffalo NAS were damaged during a brownout. I was offended by their approach (after some generous help identifying the problem, they shifted me to their paid data recovery team). I had 90% of the contents backed up and none of it was life-threatening, so I restored my 90% and set the project aside for a summer day.

Now, I've got the HDD mounted on a Mac laptop on which I've installed Ubuntu 20. I'm outside my comfort zone, and don't mind dropping a couple of bucks on a data recovery program with a straightforward GUI that I can master. (I know there are command-line utilities, but I'm non-native in the first place, and the data recover might involve a lot of hunting and pecking.)

PART ONE OF THE QUESTION can be, if you have a recommendation for such a product, please pass it along.

PART TWO is I wanted to try the product featured at [https://www.raisedr.com/](https://www.raisedr.com/) ; I have downloaded a file called raisedr.install but don't know how to run it. Cobbled together commands like *sudo apt install raisedr.install* aren't getting me any action.

Thanks in advance for suggestions.

---

### Post by Frogs Hair on 2020-07-06
Right click the .install and under permissions make sure it's executable. Try double clicking the the file and see if you get a run dialog.

---

### Post by richmilnix on 2020-07-06
In the Permissions box / Execute, the box "Allow executing file as program" is checked. I guess that's a long way of saying yes it is? I'm accustomed of course to executable files with extension .app or .exe. What does a file extension signify in Ubuntu?

When I double click, the file loads in a text editor.

---

### Post by richmilnix on 2020-07-06
Okay I get now that I can use the _**Open with**_ menu to choose different programs to use to open a file. Stabbing blindly at it, I've been unable to get good results by opening with: Ubuntu Software / Disk Image Mounter / AptURL / Software Install / Run Software. 

I also totally get that I could contact the company that authored this particular package. I was just wondering if there was a "this is how it should work" conventional wisdom for a file with extension *.install*.

---

### Post by richmilnix on 2020-07-06
never mind. file is for Debian Linux. Live and learn.

---

### Post by daniewicz on 2020-07-06
[COLOR=#4D5156][FONT=Roboto]Ubuntu is based on Debian[/FONT][/COLOR]

---

### Post by Impavidus on 2020-07-07
File extensions don't really signify anything in Ubuntu. Many files have an extension, but they are for humans and some applications. My guess is that your .install file is a shell script that you can run to install something.

Ubuntu is not Debian, but it's related to Debian. It uses the same method for managing installed software packages.

---

