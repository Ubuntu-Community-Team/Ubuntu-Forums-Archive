---
title: "Batch Renaming Of Album Tracks (BASH)"
date: 2013-05-19
forum: General Help
---

### Post by CosmicFlux on 2013-05-19
Hi,

I have a large collection of CD albums I'd like to transfer to my laptop. I've written a bash script which takes the Artist and Album names as user input and creates the relevant parent and child directory. It then rips the tracks into the directory and encodes the raw files to FLAC. I'm pleased with the script thus far, but I'd like it to  make my life even easier and name the individual track files accordingly. I'm a bit stuck on how to go about this though.

Can I create a CSV file containing the track titles and use a for loop to assign the various lines to the files? That way for any given album I'd only have to create a simple text file with the song titles. If so what kind of syntax would I be looking at?

Any help or advice would be greatly received.

Cosmic

---

### Post by Cheesemill on 2013-05-19
To rip my CDs I just use abcde, it's a command line encoder which can do everything you are asking. You'll need to install it from the repositories first...
```
sudo apt-get install abcde
```

You can run it with options directly from the command line but it's much easier to put all of your settings in a configuration file. I use the file from [here]("http://andrews-corner.org/abcde.html#flac") (just with a few path and filename alterations). Just save it as ~/.abcde.conf and edit it if you need to.

Once you've done this just load a CD and run...
```
abcde
```
and the program will look up all of the track information online (prompting you for any alterations), then rip the CD into flac and put it in the correct folder, as well as correctly tagging and renaming the files.

---

### Post by CosmicFlux on 2013-05-20
Hey,

That's absolutely 100% what I was looking to do! 

Thanks a lot for your assistance!

Cosmic

---

