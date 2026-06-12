---
title: "Troubles with Bibus - Open Office pipe"
date: 2007-10-20
forum: General Help
---

### Post by PacShady on 2007-10-20
Hey all

Having issues trying to get Bibus and OpenOffice working. It seems OpenOffice doesn't want to pipe. After much screwing around I managed to get the macro to run for setting up the UNO pipe, and set that up. However, Bibus still can't seem to connect to it. I even tried manually editing the Setup.xcu file, and that did nothing (but I get the feeling those details are out of date). I tried using the macro to change it to a socket connection, but it doesn't seem to work (clicking on the socket button doesn't change anything, and ends up with both pipe and socket buttons being selected). Bibus still says:

> Cannot connect to Openoffice. See Documentation.
Cannot connect to Openoffice. See Documentation.
Connector : couldn't connect to pipe OOo_pipe(10))

Is there any other way of making OpenOffice listen to Bibus? It's REALLY starting to irritate me. And no, I don't want to use Zotero before anyone asks me (almost every topic I found on Google in any forum had a post regarding Zotero. I have my database already set up in Bibus and that's what I'd prefer to use thank you). It's working fine on my home conputer, I just can't get it running on my laptop.

'Shady

---

### Post by PacShady on 2007-10-20
*BUMP* Because new threads tend not to be seen in this forum :(

---

### Post by pmartino on 2007-10-23
I have just upgraded to 7.10 and there is a bug or a modification in the way they handle the python-uno connector. I will post a bug report on lauchpad.
The problem is that with previous releases, the LD_LIBRARY_PATH was automatically set for python-uno and it is no more the case. The solution is to set it yourself.
Here is how to do that.

* create a file "bibus" that contains:

#! /bin/sh
export LD_LIBRARY_PATH="/usr/lib/openoffice/program"
exec /usr/share/bibus/bibus.py

1) System wide, if you have root access.
> rm /usr/bin/bibus
 put the file you just created in /usr/bin
> cp bibus /usr/bin
> chmod +x /usr/bin/bibus


2) for the current user only
add +x to the file you just created
> chmod +x bibus
You should now be able to start bibus by clicking this file.
You can of course move it in your ~/bin/ directory for instance

Pierre
Main bibus developper

---

### Post by wormie_dk on 2007-10-23
That works :-)

Super!

---

### Post by tzramsoy on 2007-10-23
worked for me, too (amd64 version). THANKS!

---

### Post by pmartino on 2007-10-25
My pleasure

Pierre

---

### Post by PacShady on 2007-10-25
I think you all have a different problem than I do. Is this referring to the errors where Bibus fails to start spitting out problems with python-uno? I'm well past that issue.

My problem is when Bibus has already started, everything LOOKS fine, but for some reason when it comes to inserting citations or formatting the bibliography, it spits back at me with the error message in my first post, as if the pipe between Bibus and OpenOffice doesn't work.

What I need is a MANUAL way of setting the pipe. I don't think the UNO Connection Wizard is working on my laptop.

'Shady

---

### Post by pmartino on 2007-10-26
> **PacShady said:**
> I think you all have a different problem than I do. Is this referring to the errors where Bibus fails to start spitting out problems with python-uno? I'm well past that issue.

My problem is when Bibus has already started, everything LOOKS fine, but for some reason when it comes to inserting citations or formatting the bibliography, it spits back at me with the error message in my first post, as if the pipe between Bibus and OpenOffice doesn't work.

What I need is a MANUAL way of setting the pipe. I don't think the UNO Connection Wizard is working on my laptop.

'Shady

Are you sure that pipe is activated in OOo and in bibus ?

1) for bibus, 
- Menu Edit/Preferences
- click the "Advanced settings" box at the bottom-Left
- Select the tab "Word processor"
- Click pipe and write down the pipe name, usually 'OOo_pipe'

2) in OOo
- Start OOo
- open /bibus/Setup/UnoConnectionListener.sxd
- Click "Get current uno connection"
- Check that you indeed get pipe and that the name is  'OOo_pipe'
- eventually change the settings THEN click "Accept UNO connections"
- Quit OOo AND the quickstarter and try again

3) If it still does not work
- start OOo with
> ooffice  --accept="pipe,name=OOo_pipe;urp;StarOffice.ServiceManager"

If it now works:
a) you can make a script to start OOo using the previous line
b) make the setting permanent by editing
~/.openoffice.org2/user/registry/data/org/openoffice/Setup.xcu
by adding
  <prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
   <value>pipe,name=OOo_pipe;urp;StarOffice.ServiceManager</value>
  </prop>
at the correct place
to help you I attached my Setup.xcu

Hope it helps,
Pierre

PS: I just tested on 7.10 the file UnoConnectionListener.sxd and it does not work anymore. I have to check that. It's a pity since the next bibus release was ready but I have to fix this bug before.

---

### Post by oswald-p on 2007-10-30
Hi pmartino,

I am trying to update the wiki I made on ubuntu-fr.org ([http://doc.ubuntu-fr.org/bibus]("http://doc.ubuntu-fr.org/bibus")) concerning the installation of Bibus on this distro.

To launch bibus, create the bibus launch file worked fine
 #! /bin/sh
export LD_LIBRARY_PATH="/usr/lib/openoffice/program"
exec /usr/share/bibus/bibus.py

Unforunately there's no connection between Bibus and OOo. I tried the 3 solutions you proposed here with no success (I have the same message than PacShady).

I hope you will be able to fix it for the next release.

regards

O-p

---

### Post by oswald-p on 2007-11-07
Finally the problem in Ubuntu 7.10 was just an OpenOffice macro security level setting.
Just go to the menu:  tools > option > security > macro security and set it to medium.

O-p

---

### Post by Jeruleus on 2007-11-12
Any update on the status of this issue?  I'm a quasi-uber-newb so I don't quite know where to find the bugreport if there is one.

---

### Post by backe on 2007-11-18
> **pmartino said:**
> Are you sure that pipe is activated in OOo and in bibus ?

1) for bibus, 
- Menu Edit/Preferences
- click the "Advanced settings" box at the bottom-Left
- Select the tab "Word processor"
- Click pipe and write down the pipe name, usually 'OOo_pipe'

2) in OOo
- Start OOo
- open /bibus/Setup/UnoConnectionListener.sxd
- Click "Get current uno connection"
- Check that you indeed get pipe and that the name is  'OOo_pipe'
- eventually change the settings THEN click "Accept UNO connections"
- Quit OOo AND the quickstarter and try again

3) If it still does not work
- start OOo with
> ooffice  --accept="pipe,name=OOo_pipe;urp;StarOffice.ServiceManager"

If it now works:
a) you can make a script to start OOo using the previous line
b) make the setting permanent by editing
~/.openoffice.org2/user/registry/data/org/openoffice/Setup.xcu
by adding
  <prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
   <value>pipe,name=OOo_pipe;urp;StarOffice.ServiceManager</value>
  </prop>
at the correct place
to help you I attached my Setup.xcu

Hope it helps,
Pierre

PS: I just tested on 7.10 the file UnoConnectionListener.sxd and it does not work anymore. I have to check that. It's a pity since the next bibus release was ready but I have to fix this bug before.



hallo Pierre,

I have the same problem, bibus and OOo can't connect. pipe is activated in bibus as well as in OOo. As you suggested I opened OOo with pipe support ( ooffice  --accept="pipe,name=OOo_pipe;urp;StarOffice.ServiceManager") and it functioned.
But then I wanted to edit the setup.xcu and hat to realize that your suggestions already existed in the file. I also tried it with your setup.xcu but that failed dispite of the fact that OOo could still be opened. Do ypou have any Idea how I could sove this problem?

thanks a lot,
Backe

p.s.; I use ubuntu gutsy

---

### Post by JohnDoc47 on 2007-12-17
Hi,

I am a total ubuntu noob but love it just the same :).  I have seen experienced the same error listed above, and applied all of the the fixes listed.  But here's the thing that made it work for me (and perhaps this was obvious) - There needs to be an OOo Writer document open for Bibus to communicate with.

This may not solve your problem, but it did for me.

---

### Post by berman56 on 2007-12-22
[COLOR="Gray"]Are you sure that pipe is activated in OOo and in bibus ?

1) for bibus, 
- Menu Edit/Preferences
- click the "Advanced settings" box at the bottom-Left
- Select the tab "Word processor"
- Click pipe and write down the pipe name, usually 'OOo_pipe'

2) in OOo
- Start OOo
- open /bibus/Setup/UnoConnectionListener.sxd
- Click "Get current uno connection"
- Check that you indeed get pipe and that the name is  'OOo_pipe'
- eventually change the settings THEN click "Accept UNO connections"
- Quit OOo AND the quickstarter and try again[/COLOR]


I am using Gusty - 7.10, my UnoConnectionListener file is at:
/usr/share/bibus/Setup/UnoConnectionListener.odg

Running that file and following the instructions in 2) above did the trick for me.

---

### Post by revdrange on 2008-03-24
I had a similar problem, 
this was resolved for me by following the first steps (ie creating the file bibus etc) 
and then in Open Office, turning the macro security to manual 
(tools options OPne.Office.Org, Macros, and setting to manual)
and re-editing the file mentioned above which sets the oo pipe
I then restarted and everything worked fine - thanks
Revdrange

---

### Post by proshanto on 2008-05-15
> **pmartino said:**
> I have just upgraded to 7.10 and there is a bug or a modification in the way they handle the python-uno connector. I will post a bug report on lauchpad.
The problem is that with previous releases, the LD_LIBRARY_PATH was automatically set for python-uno and it is no more the case. The solution is to set it yourself.
Here is how to do that.

* create a file "bibus" that contains:

#! /bin/sh
export LD_LIBRARY_PATH="/usr/lib/openoffice/program"
exec /usr/share/bibus/bibus.py

1) System wide, if you have root access.
> rm /usr/bin/bibus
 put the file you just created in /usr/bin
> cp bibus /usr/bin
> chmod +x /usr/bin/bibus


2) for the current user only
add +x to the file you just created
> chmod +x bibus
You should now be able to start bibus by clicking this file.
You can of course move it in your ~/bin/ directory for instance

Pierre
Main bibus developper


Hi Pierre,
This is not working in my case. I am using Ubuntu 8.04. I have created file "bibus", copied it to /usr/bin, chmod +x. (I saved the original file "bibus" as "bibus_old"). When I am running "bibus" it excecutes the opening menu, no problem. But when trying to do anything with Openoffice from within Bibus, it gives the same warning relating Openoffice.See documentation and oo_pipe. Any further ideas, please?
Proshanto

---

### Post by knattlhuber on 2008-07-14
Call me a noob if I'm stating the obvious:

When running the Bibus First Connection Wizard, a dialog window tells you that

"Bibus can directly insert citations in OpenOffice.org if you start OpenOffice.org in 'listening mode'."

and asks you if you want to activate this feature.

At least to me, this description sounded like a "Cite while you write" feature, which is usually do not use. So I skipped this step and subsequently got the discussed "no pipe" error message when trying to insert a citation from Bibus into OOo.

I tried all the solutions suggested in this thread, none worked.

However, after changing my OOo macro security from "High" to "Medium" (Tools>Options>OOo>Security>Macro Security) (thanks to oswald-p for pointing this out), re-running the Bibus First Connection Wizard, and then activating this feature, the connection between OOo and Bibus now works fine - with the dreaded CWYW feature though, but I'm sure there's a way to switch that off... somewhere.

---

