---
title: "How do you migrate fonts from one computer to another?"
date: 2021-03-17
forum: General Help
---

### Post by Brent_Santin on 2021-03-17
Hi!

I'm upgrading from one Lubuntu computer to a newer one. On the old system I have hundreds of vector fonts installed (TrueType, Adobe, etc.).
How can I migrate the fonts to the new computer? Is there an easy way through the UI rather than the command line?
Is there a way to just put the font files on a USB stick and bring them over to the new computer?  I don't know where they are installed on the old computer.
I do not have the original font installation files any longer.

I've looked in "/usr/share/fonts" but there only seem to be the default fonts installed by Lubuntu there, not all the custom fonts I installed. 
I also looked in my home directory. There was a folder called .fonts there but it only had one font installed by an application I had installed.

Thanks!

---

### Post by CatKiller on 2021-03-17
> **Brent_Santin said:**
> How can I migrate the fonts to the new computer? Is there an easy way through the UI rather than the command line?
Just copy them (assuming your licence allows that). The files are self-contained and not particularly big.

If you're having trouble finding where you've put them, and any of them have a unique-ish name, you can use the **locate** command to show you where it is.

---

### Post by Dennis N on 2021-03-17
Once you find your custom fonts, you can copy the font files to a USB, then copy the files to the other computer. I put my additional fonts in ~/.local/share/fonts. A family of fonts (like liberation) are in their own folder - in that case, you can copy the entire font family folder to the other computer.

---

### Post by guiverc on 2021-03-17
I'd too just manually copy mine (using command or CLI)

I have a folder on a server with all my wanted fonts.. on a new system I just add the wanted directory to 

```
`/usr/share/fonts/`
```

directory & re-create font-cache.   I don't add it to the user directory by choice, as I

- want them available for all users
- I don't want them backed up with my user files (any particularly fonts needed for a local setup will be in the user directory which will be backed up with $HOME; but fonts in that directory aren't intended to be unique to a particular box/setup/user)

If you're not sure where they are, a `sudo fc-cache -fv` may provide clues (*it'll cause the system to re-create the font cache; as the fonts are searched for, located & cache is updated; directories where they are found will be printed on screen. It'll really depend on how added, but how I add mine they'll show there as I tend to have directory names I purposely recognize*)

---

### Post by Brent_Santin on 2021-03-17
Thanks guiverc,

Using fc-cache, it showed my fonts in: 
/home/brent/.local/share

---

### Post by GhX6GZMB on 2021-03-18
Don't forget to set ownership and permissions (this often causes problems when copying user fonts between users)

Fonts in /usr/share/fonts: root:root
Fonts in /home/username/.local/share/fonts: username:username
Font directories should be set to 755, font files to 644.

---

### Post by Brent_Santin on 2021-03-19
[SIZE=4]Well, it seems that doing the fc-cache might have messed something up for Firefox on my system. I have posted about the problem here:[/SIZE]
[URL="https://ubuntuforums.org/showthread.php?t=2459491&p=14027221#post14027221"]https://ubuntuforums.org/showthread.php?t=2459491&p=14027221#post14027221
[/URL]

---

### Post by ajgreeny on 2021-03-19
There have often been perceived problems for users installing fonts in Ubuntu but this note is the content of a text-file I created years ago as an *aide memoire* and is the best way as far as I'm concerned. It has worked well for me over the past 16 years.

Fonts you will use in Ubuntu are generally stored in either of two places.
1.  /usr/share/fonts
2.  ~/.fonts
Install them in the #1 location.  If you install them to your /home directory they will not be accessible for all users on the computer, only to you.
First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/customttf
```  I am using customttf as an example and just .ttf fonts in this example.
Next open a terminal in the folder where you have a bunch of custom fonts and run command
```
sudo cp ./*.ttf /usr/share/fonts/truetype/customttf
```  This will copy the truetype fonts to that folder.
Now that we have the fonts in the proper folder we need to install them in Ubuntu.
Open a terminal in your customttf folder use command
```
sudo fc-cache -f -v
```
This will install the fonts so that your applications like OpenOffice and others can use them.

---

### Post by GhX6GZMB on 2021-03-20
> **ajgreeny said:**
> 
Fonts you will use in Ubuntu are generally stored in either of two places.
1.  /usr/share/fonts
2.  ~/.fonts


Shouldn't 2. be:
~/.local/share/fonts

??

---

### Post by deadflowr on 2021-03-20
> **ml9104 said:**
> Shouldn't 2. be:
~/.local/share/fonts

??

I don't use Lubuntu, but you can use ~/.fonts just fine in every other flavor.

---

### Post by GhX6GZMB on 2021-03-20
> **deadflowr said:**
> I don't use Lubuntu, but you can use ~/.fonts just fine in every other flavor.

Nothing to do with Lubuntu.

You can place fonts anywhere you like.

It's just that I like the association between /usr/share and ~/.local/share for global vs. user. Makes it easier to find things afterwards and to keep a structure.

---

### Post by CatKiller on 2021-03-20
FWIW, the [XDG Base Directory Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html) has ~/.fonts as a (still acceptable) legacy location, but $XDG_DATA_HOME/fonts (which is likely to default to ~/.local/share/fonts) should be used instead.

---

### Post by GhX6GZMB on 2021-03-20
> **CatKiller said:**
> FWIW, the [XDG Base Directory Specification]("https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html") has ~/.fonts as a (still acceptable) legacy location, but $XDG_DATA_HOME/fonts (which is likely to default to ~/.local/share/fonts) should be used instead.
Interesting, Thanks.
Lubuntu by default installs a ~/.local/share/fonts directory. It's empty, but still...

---

### Post by TheFu on 2021-03-21
Don't forget to backup any location with personally installed fonts as part of your backup plan. When the HDD/SSD fails, it would be bad not to have that data.

---

