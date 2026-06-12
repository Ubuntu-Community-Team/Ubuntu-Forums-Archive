---
title: "Problem cding to directory with spaces in it's name"
date: 2007-04-20
forum: General Help
---

### Post by phidia on 2007-04-20
I hesitate to post this but I wonder if someone else has run across this and has a easier solution than what I came up with.

The situation is an external drive with directories and files with spaces in their names. e.g. Report videos 00-18
I wanted to use tovid on the avi files in the main directory but in ubuntu 7.04 I couldn't cd to the directory and it seemed that the problem was that ubuntu wouldn't recognize a directory with spaces in the name. I could do 'ls' and see the directory but no matter what I tried I couldn't cd into the directory-by that I mean I know about command line compleation and tried different symbols including space for the space in the names but nothing worked. I ended up attaching the drive to a macintosh computer and eliminating the spaces in the name-then I was able to cd to the directory when I plugged the drive back into my ubuntu desktop.

How are spaces in directory and file names represented in linux-ubuntu? TIA

---

### Post by awacs on 2007-04-20
> **phidia said:**
> I hesitate to post this but I wonder if someone else has run across this and has a easier solution than what I came up with.

The situation is an external drive with directories and files with spaces in their names. e.g. Report videos 00-18
I wanted to use tovid on the avi files in the main directory but in ubuntu 7.04 I couldn't cd to the directory and it seemed that the problem was that ubuntu wouldn't recognize a directory with spaces in the name. I could do 'ls' and see the directory but no matter what I tried I couldn't cd into the directory-by that I mean I know about command line compleation and tried different symbols including space for the space in the names but nothing worked. I ended up attaching the drive to a macintosh computer and eliminating the spaces in the name-then I was able to cd to the directory when I plugged the drive back into my ubuntu desktop.

How are spaces in directory and file names represented in linux-ubuntu? TIA

I think just as they appear. Your problem, I think, is the limitation of the shell. I always use:

# cd "/usr/bin/my reports/Reports for December"

---

### Post by borahshadow on 2007-04-20
I believe I always add a \ before the space that says here is a space so it is expecting one

correct me if I am wrong

---

### Post by Nythain on 2007-04-20
yeah... i always use the \... just make sure you put the space after it, not replace teh space with it

---

### Post by phidia on 2007-04-20
I think you're saying that you add the "\" symbol as a seperation mark or in front of a space.
I didn't create these files and I can't tell people to leave spaces out of the filenames and directories they want me to work on. In my mac computer directories/files with spaces do show up in the terminal as 
Report\ /07\ /00-18
But in linux (mac is unix unless I'm confused) the names with spaces just look like spaces with no clue as to what needs to be entered to cd to them. I did try using the front and back slash symbols but it wouldn't work.

Thank you for your response.

---

