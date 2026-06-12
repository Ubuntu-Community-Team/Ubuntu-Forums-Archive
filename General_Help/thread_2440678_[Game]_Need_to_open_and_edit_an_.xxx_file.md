---
title: "[Game] Need to open and edit an .xxx file"
date: 2020-04-13
forum: General Help
---

### Post by bitsup on 2020-04-13
Hello guys and gals, nice to meet you i am bitsup, 

I am a student for software engineering that decided to fix a game "bug".

Regarding my issue it's related to the game: "Bioshock Infinite: Burial at Sea Part 1" which has key mapping issues on the game for keyboard users. Now, i went all over the files and i think i know how to fix mine and other keyboard users issue.
I've been going around the forums seeking any assistance on the issue but with no avail and what stops me in my tracks it's the following .xxx files and my last attempt at fixing the issue which, to be completely honest minor but at least i want to give it a shot.

Concerning my knowledge on the subject, it's none over the usage of .xxx files.
I would accept any help coming my way!

Greetings and have a nice day,
/bitsup

---

### Post by Impavidus on 2020-04-14
I don't know .xxx files. Wikipedia tells me that extension is used for the Singer Embroidery Format (appropriately chosen, IMHO), but of course everyone is free to use whatever extension he wishes. If the file contains plain text, you can always use a text editor. Making small changes is usually quite trivial. If it's some proprietary binary format, you could try to use a hex editor, but it's hard. If it's actually a very common format using a non-standard extension, you can determine the format that's actually used with the **file** command:```
$ file icon-sun.fubnitz 
icon-sun.fubnitz: PNG image data, 32 x 32, 8-bit/color RGB, non-interlaced
```Then use a programme that knows how to deal with that format. In case of this .fubnitz file, I'll use an image editor.

Filename extensions are used by humans and some programmes, but are irrelevant to the OS.

---

### Post by bitsup on 2020-04-15
Hey Impavidus,

I've tried your command and gives back the following:
```

DLCB_Arc_XInput_SF.xxx: Unreal Engine Package, version: 727, names: 25004, imports: 153858, exports: 1701736270

```

It seems i have to install Unreal Engine to go any further so i'll give some feedback if i manage to do it.

Greetings,
/bitsup

---

### Post by dragonfly41 on 2020-04-15
Often I can convert custom .xyz files by cloning/copying the file into say myfile.xml, or if a jar file, myfile.zip
then inspecting the contents.

For XML inspection I use XMLCopyEditor and XML is a common internal format for custom.xyz files.

---

### Post by bitsup on 2020-04-16
Hey dragonfly41,

I've tried changing the format of the file to .xml and edit it by text editor (gedit) but with no avail as the file looks half-readable and half-binary.
I would need a more detailed tutorial of what you propose.

Have a good day,
/ac

> **dragonfly41 said:**
> Often I can convert custom .xyz files by cloning/copying the file into say myfile.xml, or if a jar file, myfile.zip
then inspecting the contents.

For XML inspection I use XMLCopyEditor and XML is a common internal format for custom.xyz files.

---

