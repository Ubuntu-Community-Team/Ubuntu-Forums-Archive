---
title: "[SOLVED] need commands or script to rename files"
date: 2007-09-16
forum: General Help
---

### Post by m.musashi on 2007-09-16
I'm looking for the proper command or script that will rename many files but prefix them with the name of the folder. For example, I have photos organized in folders by date. The folder for 2006 has folders for Jan, Feb, March and so on. In these folders the pics are just named 001.jpg, 002.jpg and so on. I'd like move all the pics in the sub folders to the main 2006 folder but obviously there are a lot with the same name. I'd like to rename the pics in the Jan to be Jan_001.jpg and so on. I know I can do this folder by folder specifying the pattern but I'll have to go through a lot of folders for each year of pics.

I'd like a command that will go through the whole 2006 folder recursively and rename all the pics in the sub folders based on the name of the folder. Then it should copy them all to the parent folder (copy rather than remove so I can start over if it doesn't work right). I hope that makes sense. I know how to use find to rename or move but not how to have it choose patterns based on the name of the folder.

Thanks.

---

### Post by K.Mandla on 2007-09-16
If you're using XFCE, Thunar has a bulk renamer. I use qmv in the [renameutils]("http://packages.ubuntu.com/feisty/utils/renameutils") package, since it lets me edit the names in a text file editor or word processor ... which means I can search and replace, etc.

Are either of those options?

Edit: I've also used the [mrename]("http://packages.ubuntu.com/feisty/utils/mrename") scripts, but I thought them rather sparse.

---

### Post by m.musashi on 2007-09-16
I use gnome and I can do bulk remaning with the gthumb app but only one folder at a time and I have to specify the name pattern. I'd really rather find (since I can't write) a bash, python or something script that I can run on a folder and do it's magic on the contents.

I'll check out the links and see if anything there might work.

Thanks.

EDIT: looking over those links I don't think they will do what I'm looking for. The renameutils looks useful though so I'll keep it in mind for other tasks.

---

### Post by m.musashi on 2007-09-16
For anyone who's interested, I got a solution to this on launchpad.

[https://answers.launchpad.net/ubuntu/+question/13499](https://answers.launchpad.net/ubuntu/+question/13499)

---

