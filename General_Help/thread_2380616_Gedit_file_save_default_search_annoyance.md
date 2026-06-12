---
title: "Gedit file save default search annoyance"
date: 2017-12-19
forum: General Help
---

### Post by Robert_Gaines on 2017-12-19
I have Ubuntu 16.04. I have this annoyance when saving text files in gedit. It always starts in the Home directory so I select the Desktop folder to save my file there. When I start typing, it displays the Search text box and immediately starts to search for whatever I am typing. The behavior I am usually expecting when I click the Desktop folder is to type in the file name for the text file I am saving. At any rate, I have to click on the file name text box so I can type my file name in it. I am not quite sure why the default behavior is to start the file search when I click on the folder. I am looking for some sort of remedy for this default behavior. I normally always save everything directly to the Desktop when I am currently working on that file. Is there a setting or config file for the file explorer gedit uses so I can have it just start in the Desktop? Is there a way that I can get gedit to use Nemo as the file manager it uses for saving files? I have included a screen shot of the file explorer used by default in gedit.

---

### Post by ajgreeny on 2017-12-19
It is not a file-manager that is used when saving a file but part of the application itself and I am not aware of a way to change that.

---

### Post by HermanAB on 2017-12-20
Howdy,

Usually, if you cd to the directory you want to use by default and then launch a program, it will use that directory as the default.  I don't know whether gedit will behave the same, but it is worth a try.

Open a terminal and do:
$ cd ~/Desktop
$ gedit

Now create a new file and try to save it.

If that works, make a desktop launcher, or a little script in /usr/local/bin to launch gedit this way.

(I cannot test this - using a Mac atm)

---

