---
title: "Moving specific files from the command line"
date: 2013-02-21
forum: General Help
---

### Post by rmcellig on 2013-02-21
I have a folder that contains FLAC and MP3 files. I would like to know how to move just the Flac files to 

1. an existing folder
2. A folder I want to create

Thanks!

---

### Post by kc1di on 2013-02-21
from the terminal you can do it like this
you will have to cd to the folder where they are located first or use the complete address of the folder.

```
mv *.flac /new folder you want to move them to
```
Note create the new folder first ;)

---

### Post by foxmulder881 on 2013-02-21
> **rmcellig said:**
> I have a folder that contains FLAC and MP3 files. I would like to know how to move just the Flac files to 

1. an existing folder
2. A folder I want to create

Thanks!

As above, cd to the correct directory first.

1.

```
mv *.flac /home/*yourname*/*yourfolder*
```

2.

```
mkdir /home/*yourname*/*newfolder*
mv *.flac /home/*yourname*/*newfolder*
```

---

### Post by rmcellig on 2013-02-21
Even though I only had six test files to move, it was so fast!! Thanks so much. I had the code right before but I think I typed it wrong. This worked:

```
randy@hprandymint ~/Desktop/testflac1 $ mv *.flac /home/randy/Pictures/testflac2
```

So let me get this straight. I would have to put home/randy/Pictures/testflac2 and not /Pictures/testflac2?

---

### Post by Impavidus on 2013-02-21
> **rmcellig said:**
> So let me get this straight. I would have to put home/randy/Pictures/testflac2 and not /Pictures/testflac2?
You can use /home/randy/Pictures/testflac2 or ~/Pictures/testflac2. They are equivalent. Finally you can use a relative path: ../../Pictures/testflac2

---

### Post by rmcellig on 2013-02-21
Thanks!!

Now that I understand that. Let's say that I have five directories that contain flac files that I need to move. These directores are all in the same directory. Is there a way to move all the flac files at the same time without having to run the command for each directory? In other words is there a way to drill down into the directores to move the flac files?

I have a share folder mounted on my desktop that is from another computer. Can I use the mv commands to move to that folder? Is it just a matter of putting in the correct path?

---

### Post by SeijiSensei on 2013-02-21
> **rmcellig said:**
> So let me get this straight. I would have to put home/randy/Pictures/testflac2 and not /Pictures/testflac2?

Let's start with a couple of basics.  A path that starts with "/" is called an "absolute" path because it begins at the root of the file directory tree.  A path without a leading slash is called a "relative" path and is interpreted relative to the current working directory.  That's the directory that appears in your command prompt above, "~/Desktop/testflac1".  Since "~" is just a shorthand for "/home/randy", you're actually in the "/home/randy/Desktop/testflac1" directory.  

If you want to put files in directories under /home/randy/Pictures, the easiest thing to do is to start in that directory and work relatively to it like this.

```

$ cd ~/Pictures
$ mkdir myflacs mymp3s
$ mv /home/randy/flac/*.flac myflacs
$ mv /home/randy/mp3/*.mp3 mymp3s

```

That creates two subdirectories under /home/randy/Pictures and puts the flacs in myflacs and mp3s in mymp3s.  Notice I used absolute paths like /home/randy/flac to reference the source files.  You could replace the third line of code above with:

```
$ mv ../flac/*.flac myflacs
```

since the ".." placeholder indicates the "parent" directory of the current directory, or one level up.  "../flac" and "/home/randy/flac" both point to the same location from the perspective of "/home/randy/Pictures".

The reason why moves are instantaneous when both the source and destination are in the same filesystem is that they don't involve copying the file.  "Moving" the file in this case requires only changing the entry in the directory for the file.  If you use "mv" to transfer files to another device, say an external USB drive, actual copying is required so it will take much longer.

---

### Post by MG&amp;TL on 2013-02-21
>  
Is there a way to move all the flac files at the same time without having to run the command for each directory? In other words is there a way to drill down into the directores to move the flac files?

 
There is several ways to do this, depending on circumstances. Assuming you want all files in all five directories into just one directory and that there is only those five directories:
 
```
mv /path/to/parent/directory/*/*.flac /path/to/target
```
 
would work. Note that the first star matches any directory, and the second star matches anything ending with '.flac'.
 
>  
I have a share folder mounted on my desktop that is from another computer. Can I use the mv commands to move to that folder? Is it just a matter of putting in the correct path?
 
 
Indeed, that's one of the neat parts of *nix-based systems. I suspect your share (if you don't know where it is) is located under /media. Go take a look. :)

---

### Post by rmcellig on 2013-02-21
Thanks so much for the detailed and informative description on moving files. Much appreciated!!

---

### Post by rmcellig on 2013-02-21
Thanks MG&TL! I will try that as well.

When I move the files to the network share, they move but I get permission errors as well. Should I concern myself with this? Is there a way to avoid this when typing the mv command?

---

### Post by MG&amp;TL on 2013-02-21
> **rmcellig said:**
> When I move the files to the network share, they move but I get permission errors as well. Should I concern myself with this? Is there a way to avoid this when typing the mv command?
 
This depends. Do you have write permission to where you are moving the files? Is the share mounted by you or as root?
 
Errors usually mean the operations was aborted. Can you copy/paste output please? Thanks. :)

---

### Post by schragge on 2013-02-21
> **rmcellig said:**
> Should I concern myself with this?It depends. What error message do you get? Is it a Samba share or NFS share?

---

### Post by rmcellig on 2013-02-21
I will post the command I used as well as some of the output. It's still moving files at the moment. The command I used is actually moving all of the folders as well as all the contents of the folders instead of just the Flac files.

---

### Post by rmcellig on 2013-02-21
Here are the results from the command I used.

```
 sh-4.1# mv /mnt/home/classiccapitoljazzsessions/*/ *.flac /mnt/network/HPRANDYMINT/mosaic_flac_files
mv: failed to preserve ownership for `/mnt/network/HPRANDYMINT/mosaic_flac_files/01/14 - Eddie Miller - Who, Me.mp3': Permission denied
mv: failed to preserve ownership for `/mnt/network/HPRANDYMINT/mosaic_flac_files/01/13 - Eddie Miller - Everything, I Have Is Yours.mp3': Permission denied
mv: failed to preserve ownership for `/mnt/network/HPRANDYMINT/mosaic_flac_files/01/07 - Paul Whiteman - Wang Wang Blues.mp3': Permission denied
mv: failed to preserve ownership for `/mnt/network/HPRANDYMINT/mosaic_flac_files/01/19 - Eddie Miller & Jesse Price - Jump It With A Shuffle.mp3': Permission denied

```

---

### Post by MG&amp;TL on 2013-02-21
> **rmcellig said:**
> I will post the command I used as well as some of the output. It's still moving files at the moment. The command I used is actually moving all of the folders as well as all the contents of the folders instead of just the Flac files.
 
Is that what you want? I'm guessing not.
 
```
mv /mnt/home/classiccapitoljazzsessions/*/ *.flac /mnt/network/HPRANDYMINT/mosaic_flac_files

```
 
Should be 
 
```
 mv /mnt/home/classiccapitoljazzsessions/*/*.flac /mnt/network/HPRANDYMINT/mosaic_flac_files

```
 
Note lack of space between "/*/" and "*.flac" . Otherwise it moves all the directories in /mnt/home/classiccapitoljazzsessions/ and all flac files in the current directory to /mnt/network/blahblah.

---

### Post by rmcellig on 2013-02-21
It's always that darn space :). Thanks again. I will continue trying it out because I have so many files to convert and move.

Keep in mind that I come from the Mac way of doing things so the command line is new to me. I made a vow to myself to use the command line more because in some cases, or is that most cases, the command line is a better and quicker way of doing things.

---

### Post by MG&amp;TL on 2013-02-21
>  
It's always that darn space :). Thanks again. I will continue trying it out because I have so many files to convert and move.

 
Yup. Command-lines are famously unforgiving of typos. :)
 
>  
Keep in mind that I come from the Mac way of doing things so the command line is new to me. I made a vow to myself to use the command line more because in some cases, or is that most cases, the command line is a better and quicker way of doing things. 

 
Good attitude. 
 
Btw, why are you using the *sh* shell? Ubuntu's default is *bash* - a much more modern shell with features like more-advanced scripting, tab-completion, history search...

---

### Post by rmcellig on 2013-02-21
Busted. Sort of. I was trying it out in Ubuntu as well as Puppy Linux 5.2.8. I love the terminal better in Ubuntu than in Puppy so I was trying to do a worst case scenario. Maybe I can find a terminal like in Ubuntu that I can use in Puppy Linux.

---

### Post by MG&amp;TL on 2013-02-21
> **rmcellig said:**
> Busted. Sort of. I was trying it out in Ubuntu as well as Puppy Linux 5.2.8. I love the terminal better in Ubuntu than in Puppy so I was trying to do a worst case scenario. Maybe I can find a terminal like in Ubuntu that I can use in Puppy Linux.
 
Oh, okay. Fair enough then, I thought you'd somehow set the default shell or something. :)

---

### Post by rmcellig on 2013-02-21
I would much rather work in the Bash shell.

---

### Post by schragge on 2013-02-22
```
 sh-4.1#
```Judging from the version number, I guess it **is** the bash shell despite what the prompt says.

---

### Post by rmcellig on 2013-02-22
Hi MG&TL.

Update:v The modified code you posted works beautifully. All I keep getting are the permission denied errors (not sure how to fix this), but other than that, running smoothly! Thanks!

---

### Post by SeijiSensei on 2013-02-22
> **rmcellig said:**
> All I keep getting are the permission denied errors (not sure how to fix this),

```
mv: failed to preserve ownership for `/mnt/network/HPRANDYMINT/mosaic_flac_files/01/14 - Eddie Miller - Who, Me.mp3': Permission denied
```

What is mounted as /mnt/network or /mnt/network/HPRANDYMINT?  The latter sounds like a machine running Mint.  Are you using NFS to mount the directory?  Do you use no_root_squash in /etc/exports? 

Does the Eddie Miller file above exist in the target location?  What ownership/permissions does it have?  Or is it not copied at all?  

If you are using NFS, add "no_root_squash" to the options for the exported share in /etc/exports, then mount the drive on the client machine as root.  The easiest way to do this is to create an entry in [/etc/fstab]("https://help.ubuntu.com/community/SettingUpNFSHowTo#Static_Mounts") that will mount the remote machine automatically when the network comes up.  Make sure the two machines have identical copies of /etc/passwd and /etc/group so the mapping between usernames and user IDs is the same on both of them.

If you need more help on this issue, you should start a separate thread, as we have moved off-topic from the original question.

---

### Post by rmcellig on 2013-02-22
The Flac files copied fine. I am using Samba to share files.

Here are the permissions of a typical flac filed moved from one machine to the other.

---

### Post by rmcellig on 2013-03-05
I had to move more files from my local folder to my share folder. I can see the shared folder on the desktop but when I go to /media, I don't see my shared folder, only my external usb drive. What should I do so that I get the shared path correctly when I put it in the mv command? If the share was located under media I would simple put /media/shared folder/, but since I can't see my shared folder under media or the path back to the share, I'm not sure quite what to do.

---

