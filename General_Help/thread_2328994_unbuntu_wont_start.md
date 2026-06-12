---
title: "unbuntu wont start"
date: 2016-06-26
forum: General Help
---

### Post by Ben_E on 2016-06-26
[COLOR=#000000]Hello this started Saturday and still keeps happening every time i start the PC. Can someone give a fix . Thank you[/COLOR]

[COLOR=#000000]here is the photo of the error code.[/COLOR]

[https://drive.google.com/open?id=0B2...UQyQ1FMTWtUc28]("https://drive.google.com/open?id=0B2vUtuyhh2HlTUQyQ1FMTWtUc28")

[COLOR=#000000]Sorry about the photoquality[/COLOR]

[COLOR=#000000]I have already tryed the recovery option and that failed[/COLOR]

---

### Post by nerdtron on 2016-06-27
What did you do on the recovery mode? Did you get any errors on it?

Since the screenshot show you'll need to run fsck, then you'll need to run it to fix the file system errors. I'd recommend using the Live Desktop version of Ubuntu on doing this. So boot into Live CD mode, then open a terminal. Be sure that the internal disk (/dev/sda1) are not mounted. Then run the filesystem check.
```
sudo e2fsck -f -y -v /dev/sda1
```

It may take some time, depending on how big the drive, number of files and the errors it found. If the symptoms persists, then I'd suggest you check the hard drive health. It could be time to replace the drive itself.

---

