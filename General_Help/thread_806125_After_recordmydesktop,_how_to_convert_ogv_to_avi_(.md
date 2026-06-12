---
title: "After recordmydesktop, how to convert ogv to avi (divx)?"
date: 2008-05-24
forum: General Help
---

### Post by frenchn00b on 2008-05-24
After recordmydesktop, how to convert ogv to avi (divx)?

avidemux cannot handle the format :(

---

### Post by omababy on 2008-05-25
I dunno about divx but try something like this with mencoder for xvid:

mencoder input.ogm -ovc xvid -oac mp3lame -xvidencopts pass=1 -o output.avi

I assume if ogv has no audio just leave out the '-oac mp3lame'

---

### Post by agitdd99 on 2009-09-12
you can try using Devede [http://www.getdeb.net/app/DeVeDe](http://www.getdeb.net/app/DeVeDe) . Pick the DivX/MPEG4 disc type to convert. don't forget to raise video bit rate above 10,000 Kbit/s to gain better video quality. I'm using it in My Jaunty machine.

---

### Post by frenchn00b on 2009-09-12
> **agitdd99 said:**
> you can try using Devede [http://www.getdeb.net/app/DeVeDe](http://www.getdeb.net/app/DeVeDe) . Pick the DivX/MPEG4 disc type to convert. don't forget to raise video bit rate above 10,000 Kbit/s to gain better video quality. I'm using it in My Jaunty machine.

/usr/bin/convertogv2avi
 
```
#!/bin/bash
# ogv to avi
mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$2"
```

---

### Post by P4man on 2009-09-12
try "handbrake". Its a nice graphical program to convert video files. It has .deb packages (and I think its even in the medibuntu repo's, but not sure):

[http://handbrake.fr/?article=screenshots](http://handbrake.fr/?article=screenshots)

edit: oh, this thread is a year old. I guess the OP has already found a solution by now :D

---

### Post by la1234uk on 2009-11-14
You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR="DarkRed"]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR="DarkRed"]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR="DarkRed"]3.[/COLOR] save the file
[COLOR="DarkRed"]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR="DarkRed"]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR

---

### Post by Psumi on 2010-03-21
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR="DarkRed"]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR="DarkRed"]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR="DarkRed"]3.[/COLOR] save the file
[COLOR="DarkRed"]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR="DarkRed"]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR

Thank you, this has saved me a ton of work :D

---

### Post by AleKnaui on 2010-05-31
Really useful... THANKS!! :D

---

### Post by frenchn00b on 2010-06-02
what actually  really does : Handbrake the program?

this is unclear:
```
Screenshots
Supported Sources:

    * Any DVD-like source: VIDEO_TS folder, DVD image or real DVD (unencrypted--protection methods including CSS are not supported internally and must be handled externally with third-party software and libraries), and some .VOB and .TS files
    * Most any multimedia file it can get libavformat to read and libavcodec to decode.

```

---

### Post by JoelOl75 on 2010-06-03
Handbrake is quite upsetting.  Since the karmic version they removed avi support for some reason.  Pretty stupid if you ask me.  They say it's because there are better codecs to use now, but my neuros won't accept anything besides divx and aac or mp3 in a mp4 or avi container.  Thanks alot Handbrake devs...

---

### Post by noelvh on 2010-06-05
I used DeVeDe and it worked like a charm. I did not even try the others as I had DeVeDe installed when I read this post. I have tried this about 2 years ago and gave up then.

Noel

---

### Post by OSLinuxFreak on 2010-06-08
Tried using DeVeDe to convert my ogv file to avi and it converted really easily. But there is a problem. The original ogv file was about 1m30s in length but when DeVeDe finished it was over 4m long :confused:. Once the 1m30s mark was hit it just kept playing and showing my desktop on the screen cast. Any ideas why this would happen?

---

### Post by djtarki on 2010-07-20
> **frenchn00b said:**
> /usr/bin/convertogv2avi
 
```
#!/bin/bash
# ogv to avi
mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$2"
```

That did the trick! Thanks!

---

### Post by rmartinus on 2010-08-02
devede works for me. Have a look at this youtube tutorial:
[http://www.youtube.com/watch?v=9jqYOhpv6hg]("http://www.youtube.com/watch?v=9jqYOhpv6hg")

---

### Post by AbangBoltok on 2010-08-18
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR=DarkRed]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR=DarkRed]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR=DarkRed]3.[/COLOR] save the file
[COLOR=DarkRed]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR=DarkRed]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR

everything seems easier these days... :D :popcorn:

---

### Post by psycho5 on 2010-08-18
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR="DarkRed"]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR="DarkRed"]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR="DarkRed"]3.[/COLOR] save the file
[COLOR="DarkRed"]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR="DarkRed"]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR
Wow, thanks alot! You should make this as sticky. So easy. =)

---

### Post by philinux on 2010-08-18
VLC can convert most stuff through the gui when opening a file.

---

### Post by AlexanderDGreat on 2010-09-11
Thank you la1234uk - but sometimes, the OGV extends longer than its original. But 17 out of 18 my ogv was converted to a small XVID AVI file! Thanks.

How can I specify the width and dimensions in the script? Can you make that as well? Because I shot my desktop at only 800x600 and it produced / says it's 1024x768. It's a waste of file size in my opinion.

Can you help? Thanks. :)

---

### Post by SubCool on 2010-09-21
> **philinux said:**
> VLC can convert most stuff through the gui when opening a file.

thanks

---

### Post by tombott on 2010-09-30
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR="DarkRed"]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR="DarkRed"]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR="DarkRed"]3.[/COLOR] save the file
[COLOR="DarkRed"]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR="DarkRed"]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR

Excellent, I love a bit of bash in the afternoon.

---

### Post by Xfirebg on 2011-04-03
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR=DarkRed]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR=DarkRed]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR=DarkRed]3.[/COLOR] save the file
[COLOR=DarkRed]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR=DarkRed]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR
Thanks!:KS

---

### Post by abhithakur88 on 2011-09-13
Hi

I used above script ogv2avi, it produced avi file of 15 seconds length, but my ogv file was 18 minutes long.

Regards

---

### Post by TD-Link on 2011-09-22
> **la1234uk said:**
> You can do it with mencoder as forum people said.
I personally created a convenient ad-hoc command.
If you convert many files, you may want to do that as well. Do the following

[COLOR="DarkRed"]1.[/COLOR] create the file with an editor. Type:
 gedit /usr/bin/ogv2avi
[COLOR="DarkRed"]2.[/COLOR] type the commands in the file: 
#!/bin/bash
# ogv to avi
# Call this with multiple arguments
# for example :  ls *.{ogv,OGV} | xargs ogv2avi
N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
    echo "converting" $1
    filename=${1%.*}
    mencoder "$1" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o $filename.avi
shift 1
done
[COLOR="DarkRed"]3.[/COLOR] save the file
[COLOR="DarkRed"]4.[/COLOR] make the file executable, type:
sudo chmod +x /usr/bin/ogv2avi
[COLOR="DarkRed"]5.[/COLOR] call the command with the syntax

ogv2avi file1.ogv file2.ogv file3.ogv

you can convert many files in one go !
Cheers,

GR
really useful ... many thanks ....**^_^**

---

### Post by satturn7 on 2012-01-10
**la1234uk**

many thanks!!!

---

### Post by conualfy on 2012-07-25
For some reason, the only method that really worked for me was using PiTiVi for converting the file to something more usable.

File -> Render (select something with really high quality). Done.

---

