---
title: "&quot;maya&quot; can't call from Terminal Problem"
date: 2005-04-07
forum: General Help
---

### Post by kfc on 2005-04-07
I've installed maya under ubuntu. it runs properly except one.
I can't call "maya" from terminal.

it returns 'bash: maya: command not found'

when i try export | grep -i maya  it's shows 'bash: grep: command not found'

I understands that it might needs to have the env correctly configured. but I just don't have a clear direction to do it. I've actually added the paths needed to .bashrc , .bash_profiles, /etc/environment (as suggested from some forum).
I hope someone can help me to solve this problem. or i might need to switch distro (which is the last thing i want to do, i've just got my tablet and dual view properly setup).

At the moment, maya can still be run by typing the whole path /urs/aw/maya6.5/bin/Maya6.5. It navigates nicely and it also renders properly in render view. But when i try to do batch render from ui. or even from the terminal. It returns 'bash: maya: command not found' which clearly shows that there's no way i can do sequence renderings.

---

### Post by [S2] on 2005-04-07
Add a link in /usr/bin that points to maia like this:

cd /usr/bin
ln -s /usr/aw/maya6.5/bin/Maya6.5/maia

should work.

---

### Post by kfc on 2005-04-07
[QUOTE='[S2]']Add a link in /usr/bin that points to maia like this:

cd /usr/bin
ln -s /usr/aw/maya6.5/bin/Maya6.5/maia

should work.[/QUOTE]


it's not maia. should like to 'maya'

for comfirmation should i,
cd /usr/bin

ln -s /usr/aw/maya6.5/bin/Maya6.5/maya??
or just

cd /usr/bin
ln -s /usr/aw/maya6.5/bin/Maya6.5??

Thanks for ur kind info.

---

### Post by kfc on 2005-04-07
[QUOTE=kfc]it's not maia. should like to 'maya'

for comfirmation should i,
cd /usr/bin

ln -s /usr/aw/maya6.5/bin/Maya6.5/maya??
or just

cd /usr/bin
ln -s /usr/aw/maya6.5/bin/Maya6.5??

Thanks for ur kind info.[/QUOTE]
 here i've found a list of problems when i was installing maya.

Setting up maya6-5 (6.5-253) ...
ln: creating symbolic link `/aw/maya' to `maya6.5': No such file or directory
ln: creating symbolic link `/aw/maya6.5/bin/maya' to `Maya6.5': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libawcsprt.so' to `libawcsprt.so.1': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libpcw_opa.so' to `libpcw_opa.so.1': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libpcwfindkey.so' to `libpcwfindkey.so.1': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libpcwxml.so' to `libpcwxml.so.1': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libgcc_s.so' to `libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libstdc++.so.5' to `libstdc++.so.5.0.6': No such file or directory
ln: creating symbolic link `/aw/maya6.5/lib/libstdc++.so' to `libstdc++.so.5.0.6': No such file or directory
sed: can't read /aw/maya6.5/mentalray/maya.rayrc: No such file or directory
sed: can't read /aw/maya6.5/bin/mayarender_with_mr: No such file or directory
sed: can't read /aw/maya6.5/bin/mayaexport_with_mr: No such file or directory
mv: cannot move `/tmp/maya.rayrc' to `/aw/maya6.5/mentalray/maya.rayrc': No such file or directory
mv: cannot move `/tmp/mayarender_with_mr' to `/aw/maya6.5/bin/mayarender_with_mr': No such file or directory
mv: cannot move `/tmp/mayaexport_with_mr' to `/aw/maya6.5/bin/mayaexport_with_mr': No such file or directory

Currently my maya location in system is
/usr/aw/maya6.5/bin/Maya6.5

can anyone showing me some example on how to use the 'ln -s' command to link these stuff up?

(with my limited knowledge of linux, I've tried "sudo ln -s /usr/aw/maya6.5/bin/maya /maya6.5". But i'm not sure whether this is correct.)

btw, there's also a point in the instruction which seem not beable to follow.  

"4 - Put in the folder /usr/lib the library libstdc++-3lib6.2-2-2.10.0.so"

(quoted from [http://www.highend3d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=189551&page=0&view=collapsed&sb=5&o=&fpart=](http://www.highend3d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=189551&page=0&view=collapsed&sb=5&o=&fpart=))


I'm trying to be really careful this time without breaking the OS again.

---

### Post by luap56 on 2006-10-10
just right click on maya.bin in usr/aw/maya.bin and make link button and then copy it into usr/bin/ then rename it just maya not maya.bin rub out the bin ok worked for me:) :)

---

