---
title: "Problem running alacarte-&quot;No module named pygtk&quot;"
date: 2006-11-10
forum: General Help
---

### Post by civint on 2006-11-10
I have decided to change back to gnome, after some mishaps with Kde, and a preference for the simplicity of gnome, however, after aptitude removing KDE, I am still left with the kde bootmenu (the little graphical thing that comes up before the login screen), however, this is not the main problem (in fact, not a problem at all)

The problem i am having is with the alacrte menu editor, and also the add/remove program (although I have simply been using the packacge manager, which in fact is better for my use). When I try to run alacarte I get this error message

> Traceback (most recent call last):
  File "/usr/bin/alacarte", line 20, in ?
    from Alacarte.GnomeFront import GnomeFront
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 20, in ?
    import pygtk
ImportError: No module named pygtk

I decided to check the file > /usr/bin/alacarte and all I could find was the following (at line 20, and the following lines

> from Alacarte.GnomeFront import GnomeFront

def main():
        GnomeFront()

if __name__ == '__main__':
        main()


I should not at this point that I checked in package manager that I do in fact have python-gtk installed, which is the puzzling bit.

If anyone could  help it would be muchly appreciated.

---

### Post by christhemonkey on 2006-11-10
Try removing and reinstalling pygtk, as this error message is the one it gives when pygtk is incorrectly installed/not installed/not in the path.

---

### Post by civint on 2006-11-10
I tried uninstalling it, however, it is linked to all manner of other important packages, like ubuntu-desktop.

Anyways, I sudo aptitude removed it, and reinstalled ubuntu-desktop, which installs pygtk, and it still will not start alacarte, giving the same reason. however, it may be to do with the ubuntu-desktop install of it.

Any other ideas?

---

