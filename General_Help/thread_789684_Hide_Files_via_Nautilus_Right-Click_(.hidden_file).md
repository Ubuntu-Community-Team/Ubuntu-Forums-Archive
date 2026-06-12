---
title: "Hide Files via Nautilus Right-Click (.hidden file)"
date: 2008-05-10
forum: General Help
---

### Post by frogitts on 2008-05-10
Just a quick request: One feature that I really miss is being able to hide folders easily. I know there are cool scripts out there that one can run from a Nautilus right-click menu. Here's my suggestion:

Someone should make a short little script that adds the selected file to the folder's .hidden file, or create a .hidden file if one doesn't exist and then add the name. I would do this myself, but I'm not quite up to par on my bash skills (I wouldn't know how to pull the file name to add it into the .hidden file, and it would take me a while to figure out how to determine if a .hidden file existed yet).

Many thanks!!!

---

### Post by aroch1 on 2008-05-16
I don't know exactly how you want to do this, but are you thinking of a .hidden directory, and then moving files that you want to hide into it?  Or just changing FileName to .FileName to hide it?  I could write a script for either, but I can't exactly tell which you want.

---

### Post by PinkFloyd102489 on 2008-05-16
You dont need a script to do so. Just select the file, hit F2, and put a . in front.

---

### Post by frogitts on 2008-05-18
Right, good thoughts, but not what I was thinking. 

In Ubuntu, if one creates a file called ".hidden" and then uses a text editor to add then names of files into the ".hidden" file, those files will be hidden. The advantage of this is that it won't change the path of a file. A use for this is, for example, downloading a web page. You can add the folder with the referenced files to the ".hidden" file, and the index file will still reference them correctly.

In Windows, you can right click on a file to open up its properties and make it hidden. I'm looking for something this easy in Ubuntu, because I think Ubuntu should be better than Windows, and in this case, it's not. Not yet. Adding a "." in front of the file is one option, yes, but it doesn't always work. Adding the filename to the ".hidden" folder seems much more robust to me, but there's no easy or intuitive way to do it. You have to know that it's possible to create a ".hidden" file, create it, and then manually type in (or copy and paste) every file name you want to hide into that file, which gets old. So that's what I'm aiming for.

Right click -> scripts -> hide. Done. That would be nice :)

---

### Post by ryanhaigh on 2008-05-18
Install [nautilus-actions](apt://nautilus-actions) using whatever your normal method is (or just click the link)

Save the following code in /home/yourusername/.hidefile.sh or just save the attachment which is the same thing.

```

#!/bin/bash
#bash script to be called from nautilus actions

#change to the directory where the file is
cd "$1"

#the filename passed as the argument is added to the .hidden file
echo "$2" >> ./.hidden &&

#simulate the pressing of the F5 key to refresh the window
xte "key F5"

exit

```

Then make it executable, open terminal then:
```

chmod +x ~/.hidefile.sh

```

Open nautilus actions configuration (system>preferences>nautilus actions configuration) and add a new action with the following:
> 
**Menu Item And Action**
Label: Hide This File
Tooltip: Add file to .hidden so that it is hidden
Icon: usr/share/pixmaps/nautilus/erase.png
Path: /home/**YOURUSERNAME**/.hidefile.sh
Parameters: %d %f

**Conditions**
Filenames: *
Mimetypes: */*
Selection Contains: both
Multiple Files: unchecked (no)

**Advanced Conditions**
Only local files


Restart nautilus by pressing alt-f2 and entering nautilus -q to quite (don't do this if you are currently copying files etc) then open go to places > home or any other location to restart. Alternately you can just logout and back in. Now when you right click on a file or folder there will be a Hide This File option.

---

### Post by PinkFloyd102489 on 2008-05-18
ryanhaigh, too much script for a simple action. Open up ~/.gnome2/nautilus-scripts/ and then create a new file with the name of the script you want. Then paste this into it:

```

#!/bin/bash

touch $PWD/.hidden

echo "$PWD/$NAUTILUS_SCRIPT_SELECTED_URIS" | tee -a $PWD/.hidden

```

Much cleaner script and easier to understand what it's doing. Touch creates the file if it doesnt exist. Then the script echoes the name of the file you've right-clicked then appends it to the .hidden file in the directory.

---

### Post by frogitts on 2008-05-18
Well, I have to say, this is the best response I've gotten to a feature request ever, and makes me believe in the Ubuntu community again. Thanks guys!

Ryan's script wins in this case, because it actually added the option to my right click menu. That is, "right click -> Hide This File" instead of "right click -> scripts -> Hide this file".

PinkFloyd, I have to give you credit for innovation, but unfortunately I couldn't get your script to work. The problem is that I don't need the path to the file to be copied, just the file name. Should be a simple fix. And to be fair, your solution was what I asked for. Ryan just went above and beyond the call of duty.

The only thing is that Ryan's method takes a little elbow grease on the user end to get it working, but not much, and the result is very pretty.

So to recap, I'm just thrilled that I got two answers to this question, and that I have a really good way to easily hide files, a functionality that I've honestly been missing since Feisty. Thanks!!!

---

### Post by aroch1 on 2008-05-18
Hmm, I didn't know about the .hidden file!  You learn something new every day =) I'll definitely be putting this to good use!

---

### Post by PinkFloyd102489 on 2008-05-18
Just take out the $PWD part then. If you want it as an action, just follow what ryan posted about adding to Nautilus Actions and put the path to my script.

---

### Post by ryanhaigh on 2008-05-18
PinkFloyd, thanks for the tip but I did know about nautilus scripts, I just prefer nautilus actions from a usability point of view. What I would like to know though is why using echo for the command with %f >> .hidden doesn't work.

EDIT: I might give it a try using tee instead.

Later on I might revise this script/action so that it can be used with multiple files, unfortunately I'm not as proficient with bash as I once was, but I'll try with my new favorite language python.

---

### Post by PinkFloyd102489 on 2008-05-18
That's why I used the nautilus variable. It allows for multiple files to be packed into the variable.

---

### Post by glyphobet on 2008-11-10
Here's a script that works for me under Ubuntu 8.10:

```
#!/bin/bash

# add filename to .hidden file
echo "$1" >> "$PWD/.hidden"

#simulate the pressing of the F5 key to refresh the window
xte "keydown Control_L"; xte "key r"; xte "keyup Control_L"
```

---

### Post by cloudstrifejr1 on 2008-12-24
ryanhaigh,

I have to say, your solution was flippin great. Worked like a charm. Now I can hide all those pesky files :) Thanks!

-cloudstrifejr1

---

### Post by k6martini on 2010-01-07
I have been using Linux (mostly Ubuntu 9.04) for a few months now, but this is my first forum post. I still use Mac OS 10.5 for my main laptop and I have Netatalk and Avahi (as described in this tutorial: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) ) to allow me to use AFP between my computers. 

Using Mac OS results in the creation of a ":2eDS_Store" file on any shared directory, I have tried hiding it using the aboved described .hidden method with no luck. Anyone have any other ideas that dont require changing the file name (as it needs to stay named ":2eDS_Store" for Mac OS).

Thanks in advance, these boards have already proved invaluable with out even posting.

---

### Post by Z4mp4n0 on 2010-02-14
Thank you all for your solutions, now I can hide all those non-dotted Mac OS X generated files!
 As for k6martini's problem, you should edit your /etc/netatalk/AppleVolumes.default file and add to the line of each share "options:usedots"
ex. for home folder share:
```

~/            "Home" options:usedots,upriv
```It creates regular .DS_Store files which are hidden under both Linux and Mac OS X
I also use the upriv option for the share to use unix privileges, you could although ommit it

---

### Post by pranavkaranjkar on 2011-04-10
> **PinkFloyd102489 said:**
> ryanhaigh, too much script for a simple action. Open up ~/.gnome2/nautilus-scripts/ and then create a new file with the name of the script you want. Then paste this into it:

```

#!/bin/bash

touch $PWD/.hidden

echo "$PWD/$NAUTILUS_SCRIPT_SELECTED_URIS" | tee -a $PWD/.hidden

```Much cleaner script and easier to understand what it's doing. Touch creates the file if it doesnt exist. Then the script echoes the name of the file you've right-clicked then appends it to the .hidden file in the directory.

This is a nice script. I have one problem though. This scripts writes the entire path of the file (even when i remove the $PWD part.)
for example, it writes "file:///home/pranav/Music/cover.jpg" to the .hidden file. But for the file to hide, we need just "cover.jpg" written in the .hidden file. Can someone tell me how can I remove the other part from the nautilus variable that is being used here?

---

### Post by yaskhan on 2011-09-12
> **pranavkaranjkar said:**
> This is a nice script. I have one problem though. This scripts writes the entire path of the file (even when i remove the $PWD part.)
for example, it writes "file:///home/pranav/Music/cover.jpg" to the .hidden file. But for the file to hide, we need just "cover.jpg" written in the .hidden file. Can someone tell me how can I remove the other part from the nautilus variable that is being used here?

use grep

---

### Post by yaskhan on 2011-09-14
hide hTML folders:

#!/bin/bash 
touch $PWD/hidden
find $PWD *_files -maxdepth 0 | tee -a .hidden

HIde selected:

#!/bin/bash 
 touch $PWD/.hidden 
touch $PWD/.tmp  
echo "$PWD/$NAUTILUS_SCRIPT_SELECTED_URIS" | tee -a $PWD/.tmp
grep .*/ .tmp|sed /.*\/// > .hidden
rm -f .tmp

scripts not debugged!!!!

---

### Post by zero2xiii on 2011-09-14
I cant get any one of those two scripts working?

The first one. I have no idea why its not working? Instead of adding it directly to the menu, I just made a script in the:
~/.gnome2/nautilus-scripts
and set it as executable.

The second sript gives output of:
> /home/username//home/username/.gnome2/nautilus-scripts/Hide This File.sh 
which doesnt work either...

Am I missing something? even if I take the $PWD out, it just makes a line saying:
> file:///home/username/.gnome2/nautilus-scripts/Hide This File.sh

and that doesnt work either... if I manualy delete everything up to "Hide" then it hides the file perfectly fine... 

weird.

On ubuntu 10.04

---

### Post by yaskhan on 2011-09-15
[COLOR=Red]BUGS:[/COLOR]

**hide hTML folders:**

#!/bin/bash 
touch $[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/[COLOR=Red].[/COLOR]hidden
find $PWD *_files -maxdepth 0 | tee -a $[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/[COLOR=Red].[/COLOR]hidden

**HIde selected:**

#!/bin/bash 
 touch $[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/.hidden 
touch $[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/.tmp  
echo "$[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/$NAUTILUS_SCRIPT_SELECTED_URIS" | tee -a $[COLOR=Red]NAUTILUS_SCRIPT_CURRENT_URI[/COLOR]/.tmp
grep [COLOR=Red]-P[/COLOR] .*/ .tmp | sed[COLOR=Red] 's[/COLOR]/.*\///[COLOR=Red]' [/COLOR]> .hidden
rm -f .tmp

[COLOR=Red]**scripts not tested!!!!**[/COLOR]

---

### Post by yaskhan on 2011-09-20
[http://askubuntu.com/questions/18451/how-to-hide-in-thunar-and-nautilus-a-directory-without-putting-a-dot-in-its-nam](http://askubuntu.com/questions/18451/how-to-hide-in-thunar-and-nautilus-a-directory-without-putting-a-dot-in-its-nam)

---

### Post by psytrip on 2011-11-28
Is there similar alternative for Dolphin in KDE ?

---

