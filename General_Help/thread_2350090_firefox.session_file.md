---
title: "firefox.session file"
date: 2017-01-21
forum: General Help
---

### Post by cmcanulty on 2017-01-21
Is there any way to set firefox.session manager files t open with firefox not text editor yet still have txt files open with a text editor thank you

---

### Post by DuckHook on 2017-01-21
I would think the way to do it is with a simple shell script that calls firefox for the specific session manager files that you want rather than default to the text editor. You could further define a .desktop file for each script for real slick one-click access.

Because they are, in fact, simple text files, I don't know of a way to do it through mime types. That would affect *all* text files, which is clearly not what you want.

---

### Post by cmcanulty on 2017-01-21
I guess I don't know how to do that. So I want .txt or any text file to open with a text editor and .session files to open with firefox. But I guess linux doesn't see .session files as anything other than text. I have tried rt cl .session files and select open with firefox but then all my text files try to open with firefox.Thank you,

---

### Post by DuckHook on 2017-01-21
True. Linux is not like DOS. It doesn't actually care what the extension is. It looks at the actual file descriptor to determine file type.

I'm not a scripting guru, but let's see if I can't cobble something together&#8213;unless someone else (thankfully) beats me to the punch. :)

---

### Post by &amp;KyT$0P# on 2017-01-21
> **DuckHook said:**
> Because they are, in fact, simple text files, I don't know of a way to do it through mime types.
Just for fun, try this - create a new text document, name it "foo.c".  Create another new text document, name it "foo.h".  And another, named just "foo".  Then make sure that none of them are empty 0-byte files - if they are, fill them all with just "Foo".

See? :)

So, let's make use of this.

1) Create a file [FONT=Courier New]/usr/share/mime/packages/fx-session.xml[/FONT] and fill it with this -
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
	<mime-type type="text/x-firefox-session">
		<sub-class-of type="text/plain"/>
		<comment>Firefox session manager file</comment>
		<glob pattern="*.session"/>
	</mime-type>
</mime-info>
```

2) Run in Terminal
```
sudo update-mime-database /usr/share/mime
```

3) (Assuming Ubuntu 16.04) Add this line in [FONT=Courier New]~/.config/mimeapps.list[/FONT], under "Added Associations" -
```
text/x-firefox-session=firefox.desktop;
```

4) If it's not working, log out and back in.

Does that help?

---

### Post by DuckHook on 2017-01-22
> **halogen2 said:**
> …Does that help?
It certainly does! ;)

@OP

This is why it's so nice to have gurus like halogen2 prowling around the forums. :biggrin:

---

### Post by cmcanulty on 2017-01-22
Wow thanks that works perfectly after a logout and login. Lots of people will love this if they hear about it. Thanks!

---

### Post by &amp;KyT$0P# on 2017-01-22
You're welcome!  :KS

(@DuckHook: Me a "guru"?  Thanks for the kind words, but I have the feeling it's more like years of wrestling [this]("https://xkcd.com/1678/") type problems. ;) )

---

### Post by DuckHook on 2017-01-22
> **halogen2 said:**
> Me a "guru"?&#8230;Anyone who can spin a new mime-type from scratch is more than just an everyday garden-variety user.

FWIW, I'm stashing your post into my little collection of "keeper" threads because I've lost count of the times over the years when I've wanted to create a mime-type, but didn't know how. Yours is a marvellous little mini-tutorial.

Thanks for your contribution and Happy Ubuntu-ing!

---

### Post by &amp;KyT$0P# on 2017-01-23
Glad to help. :redface:

---

