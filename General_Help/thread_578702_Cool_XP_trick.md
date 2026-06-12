---
title: "Cool XP trick"
date: 2007-10-17
forum: General Help
---

### Post by DAFORZE on 2007-10-17
It would be cool if Ubuntu could do it too.. is it possible?

[http://youtube.com/watch?v=q6AQL55zMR4]("http://youtube.com/watch?v=q6AQL55zMR4")

---

### Post by Steveway on 2007-10-17
You can do that with the cat command.
But what do you need this for?
Hiding your "pronz" from your parents? Smuggling top secret governemt files?
I don't see the use.

---

### Post by santiagoward2000 on 2007-10-17
Cool, I'll use it next time I feel the CIA is watching me...8-)

---

### Post by thirddeep on 2007-10-17
google for steganography, it's far more interesting than concatenating a compressed archive at the end of a jpg :-)

Thd.

---

### Post by cmost on 2007-10-17
One minute in Google yielded this:

1) Find picture: picture.jpg
2) Create your ZIP or TAR or RAR or any compressed archive; using Gnome’s Archive Manager. We’ll use secret.zip for this example.
3) In a terminal type: cat secret.zip >> picture.jpg (This appends the zip to the end of the jpg file.

Now the file looks and feels like a jpg… however, Archive Manager doesn’t know what to do with it. So before opening with Archive Manager change the extension to .zip (or to the appropriate extension for the archive type you used; i.e., rar, tar.gz, etc.) and it should open just fine!

---

