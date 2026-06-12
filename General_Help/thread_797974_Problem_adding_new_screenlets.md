---
title: "Problem adding new screenlets"
date: 2008-05-17
forum: General Help
---

### Post by Utnubuster on 2008-05-17
So I'm trying to download the xbox live screenlet 


(see; [http://screenlets.org/index.php/Xbox_Live_Gamercard](http://screenlets.org/index.php/Xbox_Live_Gamercard))

The instructions are **Install as usual by extracting the contents of the screenlet's archive to the directory "$HOME/.screenlets". **

I'm unsure how to do this a .py file can be run in the terminal but it fails. Heres a shot. the photo taker may be in the way 

[http://i93.photobucket.com/albums/l48/J0ey790/ummmm.png](http://i93.photobucket.com/albums/l48/J0ey790/ummmm.png)

Any help would be gladly appreciated I'll log on tomorrow thanks!

---

### Post by EXCiD3 on 2008-05-17
Simple, if you saved it to your desktop, right click the archive and click "Extract Here". Right click on the folder it just created and either Cut or Copy. Open up your Home folder and press Ctrl-H to view hidden files/folders. You should see a .screenlets folder now. Paste inside that folder and then you should be able to use it in screenlets now.

---

### Post by Utnubuster on 2008-05-18
Thanks! So far so good except the screenlet won't start it shows it and stuff but it wont pop-up. Not just the gamercard its for some others too. Stuff like the clock and notes pop-up  instantly

---

### Post by EXCiD3 on 2008-05-18
Go back into the folder where the screenlets are located and try making them executable: Right click the file > properties > permissions > allow as executable.

.py files are python scripts that are run when you choose to display the screenlet. sometimes these just need to be made executable!

---

### Post by Utnubuster on 2008-05-19
the .py was already executable. Still nothing but I'll just leave it for now I guess. Thanks for the help too, Ubuntu forums is so helpful:)

---

### Post by igster on 2008-05-19
I was able to just drag it into the screenlets window to install.  I got a warning but it still worked.

> MyGamercard was not packaged with the screenlet packager. Do you wish to continue and try to install it?Click Yes.

> The MyGamercardScreenlet has been succesfully installed.It then showed up in the list of available screenlets.

Hope this helps.

---

### Post by EXCiD3 on 2008-05-19
> **igster said:**
> I was able to just drag it into the screenlets window to install.  I got a warning but it still worked.

Click Yes.

It then showed up in the list of available screenlets.

Hope this helps.

I think it may be another problem because he got it installed fine it just wont load correctly. You can definitely try dragging it over into screenlets and try it, but since other screenlets dont work it might be something else. Try completely removing screenlets from synaptic and deleting your .screenlets folder and then reinstalling them (along with mygamercard). Hopefully that will clear up any misconfigured things that could prevent some of them from running. I had a problem like that a while back but i ended up ditching screenlets in favor of conky, its much cooler looking and reliable. :popcorn:

---

