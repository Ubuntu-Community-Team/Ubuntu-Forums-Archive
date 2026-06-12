---
title: "how do I add to sources.list using terminal"
date: 2006-12-01
forum: General Help
---

### Post by helmeteye on 2006-12-01
I used the automatic sources.list generator on the ubuntu page but don't know how to add the generated  sources list manually.  I could cut and paste the sources in synoptic but I don't want to do that.  I am also curious, what is the command wget and when and why use it.  I have looked for instructions but have had problems finding the right ones.

---

### Post by styracosaurus on 2006-12-01
Your system's sources.list file is in this dir: /etc/apt/sources.list.
Using the terminal, you can type:

$ sudo gedit /etc/apt/sources.list

And copy and paste it in gedit. You could also use any other text editor, whatever you like and have installed.

As for wget, it's a powerful HTTP and FTP client. You can use it to download normal webpages, files, etc. Here is an example of it's awesomeness:

$ wget -r -l1 --no-parent -A.mp3 [http://www.lemondemon.com/lemondemon/](http://www.lemondemon.com/lemondemon/)

This will download all of the sample mp3s on the band Lemon Demon's website. Try "man wget" on the command line for more info, and explanation of each option above.

Hope I helped!

---

### Post by Shatrat on 2006-12-01
In a terminal you need to use an editor like vi or emacs or nano.  Nano is probably gonna be a lot easier to learn how to use than the others.
Just type ```
sudo nano /etc/apt/sources.list
```

---

### Post by helmeteye on 2006-12-01
Thanks yall.  I did the nano thing but how do I save the sources.list?  I tried control x and thought it saved but it didn't.

---

### Post by LLRNR on 2006-12-01
Either Ctrl+X ( = exit ) then confirm ('y'), either Ctrl+O ( = write out = save ) and then Ctrl+X for exit.

---

### Post by styracosaurus on 2006-12-01
In nano, use ctrl-o to save first, then ctrl-x.

---

### Post by helmeteye on 2006-12-01
Cool, I didn't know control o.  I used control x and then "y".  Thanx.  That is probably what I needed.

---

