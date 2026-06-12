---
title: "Batch convert .wma to .mp3, keep filename"
date: 2007-09-22
forum: General Help
---

### Post by mykrob on 2007-09-22
Hey-

I have 23 .wma files that I wouldl ike to convert to .mp3 files. I am looking for a console based (or gui, whatever) solution to batch convert as stated above,but maintain the filename, except switch the file extension upon conversion.. Help?

Thanks,
-myk

---

### Post by AndyCooll on 2007-09-22
Well you can't simply change the file extension, mp3 and wma are different encodings and you are going to have to re-encode those files. This will undoubtedly mean some loss of quality and usually isn't recommended. I've never tried it but I think something like soundkonverter will do that if you *really* must.

:cool:

---

### Post by Gwasanaethau on 2007-09-22
I have one, first you'll need to get 'soundconverter':

```
sudo apt-get install soundconverter
```

Then you can use the following command to convert them:

```
soundconverter -b -m audio/mpeg -s .mp3 <your wma tracks>
```

Hope that helps you dude!

EDIT: Sorry, didn't see you were using Kubuntu - I guess soundkonverter will do the same.
And yeah, I agree with AndyCooll, changing from one lossless format to another can't be good for the quality - most of the audio players should play wma with the right codecs installed.

---

### Post by mykrob on 2007-09-22
thanks. I understand they will need to be converted, what i meant by  the filename was so i wouldnt have to go back through and rename every file, the converter would keep the naming convention during conversion..

I will try soundkonverter.

---

