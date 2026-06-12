---
title: "Open shortcut from terminal"
date: 2008-05-18
forum: General Help
---

### Post by mistersam on 2008-05-18
I used prism to create a shortcut to Remember the Milk. Now, I would like to ba able to open this from the terminal with a simple command such as "prism-rtm"

However, as it stands now, I have to either click the shortcut button or enter

```
xulrunner-1.9 /usr/share/prism/application.ini -webapp remember.the.milk@prism.app
```

which is a bit too long. Any ideas?

Thanks

---

### Post by joshsmith on 2008-05-18
hey

you could do this:
make a script with the command you want to run, save it in a text file, put it in a folder in your path (you can change where you path is, and have multiple folders, but for ease lets just call this putting it in the folder /usr/local/bin) and then make it executable

this is the placce where applications get stored, so now you can run it just by typing in the name of you script, so if you save the text file as
prism-rtm
and have the contents as
xulrunner-1.9 /usr/share/prism/application.ini -webapp [email]remember.the.milk@prism.app[/email]
you are all done

remember this would work for any terminal command, allowing you to do great things like automate almost anything

---

### Post by mistersam on 2008-05-18
Excellent! This is exactly what I was looking for. Thank you.

---

