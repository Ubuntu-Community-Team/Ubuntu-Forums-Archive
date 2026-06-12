---
title: "Trying to install 'Leipzig' into scidvspc-hkvc/snap [Solved]"
date: 2021-08-31
forum: General Help
---

### Post by al53 on 2021-08-31
Hi,
 

 I installed from snap a fork of scidvspc wich is called scidvspc-hkvc it is ok but do not have the stile of pieces i want “Leipzig” so i went to Sourceforge and i got the file i needed: goldenbergg_high_dpi_pieces_v2 (leipzig is inside, among many others) and i downloaded it into my system (in Spanish Descargas/Downloads).

 

 In order to get the installation of leipzig into scidvspc-hkvc this is what i did without any result, after a reboot:

 

 I created a folder named "pieces" made like this:

```
$ mkdir /home/keos/snap/scidvspc-hkvc/5/.scidvspc/pieces
```

 

  

And after that the Leipzig file should be copied to the new "pieces" file, is it not so?:

```
cp /home/keos/Descargas/goldenbergg_high_dpi_pieces_v2/Leipzig.tcl /home/keos/snap/scidvspc-hkvc/5/.scidvspc/pieces
```
 
I tried this via too:

```
$ mkdir /snap/scidvspc-hkvc/current/.scidvspc/pieces
$ cp /home/keos/Descargas/goldenbergg_high_dpi_pieces_v2/Leipzig.tcl /home/keos/snap/scidvspc-hkvc/current/.scidvspc/pieces
```


*All of the above following more or less the guidelines of another forum, not necessarily because I know what exactly I am doing, I am less than an average user.



 What m”i doing wrong?
 

 Thanks for any advice, help.

And it is there,

---

### Post by grahammechanical on 2021-08-31
Did Leipzig.tcl actually copy over to the pieces folder? What did you do next? Run scidvspc-hkvc? What instructions does this Chess program give for adding additional chess piece styles?

As this is a snap packaged application you could try opening Ubuntu software and finding the scidvspc-hkvc page. You might find that there is a tab allowing you to set permissions. It might include something useful for getting added chess piece styles recognised by the program.

Regards.

---

### Post by al53 on 2021-09-01
It was done in the other operating system that I have by following those instructions that someone gave me in another forum. 

 There is nothing about this somewhere, it is a common thing that people do to their liking (if you know how to deal with it).
 

 What is supposed to be done later? Just a reboot of the system and when the program is opened, the option must already be included in the corresponding tab.
 

 As I said before, there is nothing anywhere that is specified to follow in this case since in general the program already comes with its pieces styles assigned by default by the program developer. 
 This is something extra that you want to do, like when you have an operating system that comes by default with ... and you want to change to ...

I'm probably doing something wrong here ... :(


EDIT:
Just in case anyone can understand that you are talking about the customary permissions for packages -- the permissions are marked positively.
Other permissions, as I said before, are not indicated anywhere. 
Then there is the fact that it was installed and continues to work correctly on the other operating system.

I repeat myself, I have done something wrong.

---

### Post by al53 on 2021-09-02
I found the way out by going into thunar and moving the file 'peices' on top of the list, in order to be the first ...

Reboot the system, and it was already created/installed in the graphic of scidvspc-hkvc.

---

