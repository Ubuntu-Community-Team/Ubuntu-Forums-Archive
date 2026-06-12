---
title: "HOW TO: Download videos from your tivo"
date: 2007-12-28
forum: General Help
---

### Post by Afkpuz on 2007-12-28
This guide will show you how to pull your recordings off of your tivo DVR and convert them into mpg files.
1.) Find you MAK (media access key)-Turn on your tivo and goto Messages and Settings>Account and System info>Media Access Key.  Write this down!

2.)  Get on your computer and open a web browser.  Make sure that this tivo is on the same network as your computer.  Goto
[https://192.168.0.190](https://192.168.0.190)

3.) Click through any security warnings and enter "tivo" (without quotes) as your user name.  Your password is the MAK that you got from step 1.

4.)  Now, you should see a web server containing all the recordings on your tivo.  Select the file you wish to download and click "download" on the right.  I recommend using a download accelerator for this.  Even though tivo is on your network, it does not download at network speeds.  Speed it up as much as possible.

5.) You're almost done.  Now, you'll need to convert the .tivo file into something you can actually watch.  Download this 
[http://sourceforge.net/project/downloading.php?group_id=183716&use_mirror=superb-east&filename=tivodecode-0.1.4.tar.gz&89060555](http://sourceforge.net/project/downloading.php?group_id=183716&use_mirror=superb-east&filename=tivodecode-0.1.4.tar.gz&89060555)

Just in case you don't know how to install a tarball...
Create a folder in your home folder called "Installs".  Extract the tar into there.  Then, open a terminal
```

sudo apt-get install build-essential
cd Installs/tivodecode-0.1.4
make
sudo make install

```

6.) Now to convert.  Move your tivo file into ~Installs/tivodecode-0-1.4/objects.dir
Then run this command.

```
./tivodecode -m XXXXXXXXXX -o output.mpg input.TiVo
```

Replace XXXXXXXXXXXXXX with your MAK
Replace "output" with the name you want to give the file.  Remember to leave the .mpg
Replace "input" with the name of your .tivo file.  Make sure to leave the ".Tivo"

If you did everything correctly, it should work for a minute or two, then produce a watchable mpg file!  And please note that even though the thumbnails of your new mpg files might look out of proportion, just change the aspect ration in your video player to the correct size and they should look normal.  Enjoy!

---

### Post by billycub on 2008-02-28
There's also a GUI utility for Ubuntu called "Tivo 4 Tiny" at [http://tivo4tiny.sourceforge.net](http://tivo4tiny.sourceforge.net) which lets you download files and also converts formats.

---

### Post by BryceHarding on 2008-05-19
cannot get this to work. i have downloded tivodecode-0.1.4 as directed and extracted to a folder with ubuntu archive manager. when i cd to the tivodecode-0.1.4 folder i run make and seems not to get errors.

tried sudo make install and get:

```
make: *** No rule to make target `install'.  Stop.
```

googleing this output yeields nothing i can make any sense of.

any ideas?

---

### Post by BryceHarding on 2008-05-19
the .deb files at the tivo4tiny project on SourceForge all seem to be for i386 architecture. not sure how to get this to work on x86 intell syestem. anyone know how this can be achieved?

---

### Post by Afkpuz on 2008-05-20
Thanks.  I didn't know that it was only an i386 thing.  You might see if you can track down who wrote the code.

---

### Post by pbpersson on 2008-05-21
I was following another guide and got this all to work.....however when I use TiVoDecode to convert the movies into mpeg format, the video is all choppy.

I did this on a 64-bit AMD version of Hardy Heron

Will this only work properly on a 32-bit OS version?

Please advise

---

### Post by billycub on 2008-05-21
> **BryceHarding said:**
> the .deb files at the tivo4tiny project on SourceForge all seem to be for i386 architecture. not sure how to get this to work on x86 intell syestem. anyone know how this can be achieved?

The .deb files for tivo4tiny work on any 32-bit Ubuntu x86 system, not just i386.  They won't work if you are using 64-bit Ubuntu; I don't have a 64-bit machine so I can't make .deb's for that architecture. (I am the author of tivo4tiny but not the author of tivodecode, which does the heavy lifting)

---

