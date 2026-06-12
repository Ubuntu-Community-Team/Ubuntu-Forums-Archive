---
title: "Gwibber facebook bug."
date: 2013-02-15
forum: General Help
---

### Post by Enigmapond on 2013-02-15
Hi..
I am aware that there is an ongoing bug with gwibber not being able to authorise properly with facebook. Status's can be updated but nothing else shows. I was wondering if anyone has a workaround for this?

Thanks!

---

### Post by Mr.Dunham on 2013-03-01
Hi,

I've been pulling my hair for months because of this issue. :P

Thanks to comment #79 here: [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672)
there's a workaround/fix to this, and guess what... IT WORKS! :D
Just checked it and now I can see my Facebook feed on Gwibber.

It's here, [http://planetared.com/2013/01/solucionar-error-de-facebook-en-gwibber-para-ubuntu-12-04-y-12-10/](http://planetared.com/2013/01/solucionar-error-de-facebook-en-gwibber-para-ubuntu-12-04-y-12-10/)
it's in Spanish, but if you guys can't understand, I'll do a quick translation:


> Open the file /usr/share/gwibber/plugins/facebook/__init__.py with Gedit or other text editor, this way:
```
gksu gedit /usr/share/gwibber/plugins/facebook/__init__.py
```
Now find the following line:
```
m["privacy"]["description"] = data["privacy"]["description"]
```
and replace it with the following lines exactly (including the indentations -two blank spaces- before the two "m"s):
```
if data["privacy"].has_key("description"):
  m["privacy"]["description"] = data["privacy"]["description"]
else:
  m["privacy"]["description"] = "Unknown"
```
Save the file and restart Gwibber via the following commands:
```
killall gwibber-service
gwibber-service &
```
This fix works for 12.04 and 12.10

---

### Post by markbl on 2013-03-02
It's simpler and better python code to replace those 4 lines with:
```

m["privacy"]["description"] = data["privacy"].get("description", "Unknown")

```

---

### Post by Mr.Dunham on 2013-03-02
Thanks for pointing it out, markbl. I don't know anything about code, so I just replicated a solution someone else found on the web.

---

