---
title: "How to install Etcher image Writer"
date: 2016-05-18
forum: General Help
---

### Post by RobGoss on 2016-05-18
Hello everyone, I was wondering if anyone here knew how to install this new **image writer tool** I came across for Linux [http://www.etcher.io/](http://www.etcher.io/) I've try Googling it but did not find anything that states how to install it
 
It states after granting access and making the file executable and running it as so **>** **Allowing executable file as program **you should run the following two commands but nothing seems to happen when I do **. **Thanks so much

> [CENTER][COLOR=#333333][FONT=Menlo]$ chmod a+x Etcher-linux-x64.AppImage[/FONT][/COLOR][/CENTER]



> [CENTER][COLOR=#333333][FONT=Menlo]$ sudo ./Etcher-linux-x64.AppImage[/FONT][/COLOR][/CENTER]


---

### Post by vasa1 on 2016-05-19
According to [this page]("http://appimage.org/") in the *Now What* section, you may need to insert ***** just before **.Appimage**. 

> To run an AppImage, simply:

Make it executable

```
$ chmod a+x Subsurface*.AppImage
```and run!

```
$ ./Subsurface*.AppImage
```

So I imagine you'd use

```
$ chmod a+x Etcher-linux-x64*.AppImage
```and
```
$ ./Etcher-linux-x64*.AppImage
```

Note the lack of *sudo* in the second command!

All the best.

BTW, *Subsurface* has to do with Linus Torvalds who is an avid diver :)

And more apps are listed here: [https://bintray.com/probono/AppImages](https://bintray.com/probono/AppImages)

---

### Post by RobGoss on 2016-05-19
Thanks for the reply, Vasa

It seems when I try to run the first command it will not completely run It tells me the Directory cannot be found, and the second command does not run also. I'm not sure what I'm over looking

Is there anyone else using this tools that might shed some light on how to set it up,

---

### Post by vasa1 on 2016-05-19
Okay, I can get a small package, Leafpad, to work.

1. Visit [http://appimage.org/](http://appimage.org/). That points you to a page from where you can download AppImages: [https://bintray.com/probono/AppImages](https://bintray.com/probono/AppImages)

2. When there, look for the AppImage of interest. There are currently five pages. Etcher is on page 2 and Leafpad is on page 3. I went for Leafpad.

3. Click on the Leafpad icon. You're taken to [https://bintray.com/probono/AppImages/Leafpad/view](https://bintray.com/probono/AppImages/Leafpad/view).

4. Here, click on the "Files" tab. Then, click on the first file in the list. It should be the only one ending in exactly .AppImage. It will be downloaded to your browser's default download folder. From there, move it to wherever you want.

5. Once that's done, right-click on the file (using your file manager's GUI) and change its permissions to make it viewable, changeable, and executable only by you (owner).

6. Double-click on the file. Before it opens, you'll be asked if you want to create a .desktop file. I chose not to. Then the program opens.

7. If you don't like using your browser interface to download the file, an alternative using *curl* is provided. *curl* may not be installed on your system, so install that first. The command I used from *the destination folder* is this:```
$ curl -L "https://dl.bintray.com/probono/AppImages/Leafpad-0.8.17-x86_64.AppImage" -o LEAFPAD.AppImage
```
I think the prefix in "LEAFPAD.AppImage" is not that important.

There are some interesting apps in there. LibreOffice 5.1.2 is there! As is Chromium 51.0.2684.0.

The most obvious caveats are that you trust whoever is providing the AppImage and that the image may not reflect the latest version. For example, the Leafpad version listed there is slightly older than the one that comes with Lubuntu 16.04. On the other hand, GIMP is at 2.9.3 whereas the standard repo has 2.8.16.

---

### Post by RobGoss on 2016-05-19
Vasa1, wow thanks so much for the info and your time question? Do you have this installed on your system and if so how do you like it.

I'll try this method as soon as I get home much appreciated

---

### Post by vasa1 on 2016-05-19
> **RobGoss said:**
> Vasa1, wow thanks so much for the info and your time question? Do you have this installed on your system and if so how do you like it.

I'll try this method as soon as I get home much appreciated
Well, that's what I did. The procedure I described is what I used to install Leafpad both via the browser and via *curl*. Both worked. I'd be more comfortable using curl than the browser if the browser doesn't have a "resume" option. Some of the AppImages are going to be pretty hefty.

---

### Post by RobGoss on 2016-05-19
Thanks so much for all the help I'll see if i can get it installed

---

