---
title: "Bibus Ubuntu Howto"
date: 2005-07-21
forum: General Help
---

### Post by tommaso.bianchi on 2005-07-21
Hi, here follows an howto for getting bibus bibliography utility to work with hoary.


Thanks to Pierre Martineau for letting us use this fantastic app!


bibus site:
[http://bibus-biblio.sourceforge.net](http://bibus-biblio.sourceforge.net)



1) Install from Ubuntu (universe required)
python2.4
libwxgtk2.5.3-python_2.5.3.2
python-sqlite_1.0.1

2) Now install from the Bibus site
dpkg -i openoffice-pyuno_20050203-1_i386.deb
dpkg -i --force-all bibus_1.0.0-1_all.deb bibus-doc-en_1.0.0-1_all.deb

3)
Now, you must fool the system by telling it to use python2.4 instead of 2.3
for this you must create a link in
/usr/lib/openoffice/program

As root:
> cd /usr/lib/openoffice/program
> ln -s /usr/lib/libpython2.4.so libpython2.3.so.1.0

Start Bibus  by pressing ALT+F2 and type "bibus"

---

### Post by rsay on 2005-07-21
Thanks,

This was incredibly timely. I had attempted to install this program only yesterday. I needed to make one change to get things to work properly which appears to be a typo in the original post.

```
ln -s /usr/lib/libpython2.4.so.1.0 libpython2.3.so.1.0
``` 

After that it worked like a charm.

---

### Post by pyropir on 2005-08-23
thanks a lot for this how to. I used the ubuntu package available from the Bibus site and didn't have the Python issue. I only had one additional problem to sort out to get integration of Bibus with OO.o to work. I'm using a MySQL database. When I tried to configure  the ODBC connection in Tools/Data sources, I got the following error: "Could not load the program library libodbc.so.1 or it is corrupted. The ODBC data source selection is not available." 

To get it to work, I needed to create the following link:

ln -s /usr/lib/libodbc.so.1 /usr/lib/libodbc.so

---

### Post by ulugeyik on 2005-09-12
Hello,

I have tried all the instructions here and elsewhere with no success. It seems like OpenOffice 2.0 may be the part of the problem. I do not see any menu options in Bibus nor in OpenOffice that would let me insert any references.

Here is what I did:

1) added these to my sources.list:
## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./


2) downloaded:
bibus_1.0.0-1_all.deb  bibus-doc-en_1.0.0-1_all.deb  libsqliteodbc_0.64-1_i386.deb
and installed them with dpkg -i and run apt-get install -f  to fix the dependencies.

3) 
for bibus to talk to openoffice
emacs ./usr/lib/openoffice2/share/registry/data/org/openoffice/Setup.xcu

after this
<node oor:name="Office"/>
inserted this 
<prop oor:name="ooSetupConnectionURL" oor:type="xs:string">
<value>pipe,name=OOo_pipe;urp;</value>
</prop>

4) cd /usr/lib/openoffice2/program
ln -s /usr/lib/libpython2.4.so.1.0 libpython2.3.so.1.0
ln -s /usr/lib/libodbc.so.1 /usr/lib/libodbc.so


am I missing something here?

---

### Post by istaon on 2005-10-30
Hello together,

I tried to install bibus for openoffice2 (ubuntu breezy) and .... I succsess :)
What I,ve done? Now It's quite easy, so here is the solution:

Install bibu as discribed above.

After that you have to set two symlinks:

ln -s /usr/lib/openoffice2 /usr/lib/openoffice

ln -s /usr/lib/openoffice2/share /usr/lib/openoffice2/user

Than start bibus as root

sudo bibus

And configure it for your needs. If you seleced sqlite, than you have to change the filepermissions after exit to your needs...

That's all.

So far as I know is everything working, when not, please let me know.

---

### Post by elbast on 2005-11-24
i'm runing a ubuntu 5.10 . and i'm very interested in this bibus.
the explications above seem very clear, but i cannot get the packages (libsq... and pyth...), although i add the following links to my sources.list
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

any idea??

thanks !
:)

---

### Post by sethmahoney on 2005-12-13
I'm also running Breezy, and am having the same problems mentioned in the above post.  Any ideas?

---

### Post by elbast on 2005-12-14
ok, I fixed the problem that way:

1) check with Adtept that python-wxgtk2.6 is installed
2) download the package from bibus site
3) from the command shell, do
 > dpkg &#8211;force-all -i bibus_1.1.0_all.deb
4) If you want to use it with OOo2, you will have to edit the
file /usr/bin/bibus and replace in it the paths
(replace ../openoffice/.. by ../openoffice2/..)

but i still have problems while using it:
- i can't export the reference to Oo2
- i can't import endnote files

if, after having installed it and used it, you find the solution for these two things, please let me know :-) !

good luck !

---

### Post by GrumpyBob on 2005-12-27
Well, I have to say that Bibus is a fine piece of software.  Fine, that is, once it's running.  I eventually got it up and running with Ubuntu 5.10.  But my root partition got trashed and I have had to reinstall breezy.  So I also have to reinstall bibus, which is proving a real trial.

What is involved with making an Ubuntu deb package from the whole thing?

It would be so much easier than going through this whole palaver once more! 
I've spent most of this morning trying to persuade bibus to install, with few signs of success on the horizon.  

At the moment, sudo dpkg -i openoffice-pyuno_20050203-1_i386.deb fails because python-uno is already installed, and cannot be uninstalled without uninstalling OOo2.  

Robert

---

### Post by elbast on 2005-12-27
Hi,
if python-uno is already installed, why would you install it a second time?? 
I would leave it like that if i were you...
but as you seemed to have used bibus, could you please tell me if you were able to export your references to Oo2 and to import endnote files?
and i have an another question that is not about bibus: when you reinstalled ubuntu after your root partition crashed, did your home partition remained safe, and the programmes found their previous data (like your mails if you used Kmail etc...)?
good luck for your bibus re-installation.

---

### Post by malmjako on 2006-01-09
[QUOTE=elbast]but i still have problems while using it:
- i can't export the reference to Oo2[/QUOTE]
By "export the reference", do you mean when you choose "Finalize" in the OpenOffice.org menu? In that case I have the same problem. It just stalls a short bit through the process and I have to manually kill bibus. I need to be able to save the document in Microsoft Word (.doc) format, but when I do, the bibliography disppears (after closing the document). Any possible solutions?

---

### Post by Eric DANE on 2006-01-25
I successfully installed bibus_1.1.1-1 on Ubuntu 5.10 following the procedure in [Bibus page on Ubuntu Wiki]("https://wiki.ubuntu.com/Bibus") by :
```
sudo dpkg -i --force-all bibus_1.1.1-1_all.deb
```.

But the package is declared "broken" by Synaptic. Then no more upgrade is possible :(

---

### Post by jouke.postma on 2006-02-25
I just installed bibus 1.1.1-1 on a fresh install of Dapper Drake. To avoid having a broken package on my system (as the wiki suggests [https://wiki.ubuntu.com/Bibus](https://wiki.ubuntu.com/Bibus)) I removed the dependency on python by editing the control file in the debian package**. It installed fine. I had to edit the bibus startup script (/usr/bin/bibus) and adjust the path of openoffice to openoffice2. Also had to open  /usr/share/bibus/Setup/UnoConnectionListener.sxd to establish the pipe (this should normally happen during the installation wizard). 

**note, There is probably a better way to do this but this is how I did it: open debian package in file roller (just double click on it) - extract the control.tar.gz (drag & drop) - open the control.tar.gz and extract the control file in ./ - edit the control file - delete the original control file from the package (select and press delete). - drag the new control file file roller, but not into the ./ folder (since file roller will give an error) but to the root of the archive - close the archive and open the debian package again - delete the original  control.tar.gz - drag the new control.tar.gz into file roller.

---

### Post by asdir on 2007-10-04
I was wondering if someone could update this thread to the current version of bibus and to feisty/gutsy.

Also I was wondering if these issues are what is keeping bibus from being added to the official repositories. Are they?

---

### Post by drorlev on 2008-03-15
Here is a link to a version dealing with Feisty / Gutsy: [http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu")

dror

---

