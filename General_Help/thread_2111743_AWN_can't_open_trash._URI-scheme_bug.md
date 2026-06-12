---
title: "AWN can't open trash. URI-scheme bug"
date: 2013-02-02
forum: General Help
---

### Post by SteveDeFacto on 2013-02-02
So I've pretty much had Xubuntu 12.10 configured just how I like it using AWN for the last few months. However, there is one tiny bug that I was never able to solve. When I click on the Garbage applet in AWN it says: Unable to detect the URI-scheme of "trash:".

Any idea what is wrong and how I can fix it?

---

### Post by SteveDeFacto on 2013-02-08
bump

---

### Post by undrline on 2013-06-18
bump. 

I'm using Garbage 0.4.1 with the most recent version of AWN in the repositories on XUbuntu 12.04.2 with XFCE 4.10.  It does say in the about of the applet that the author of the applet is
Mark Lee and gives an email address, so it might be easier to contact him directly ...

---

### Post by afredco on 2013-10-14
Has anyone made any progress on this? I have AWN on 12.04 and it works.  On a Mint15 system (13.04) AWNgarbage applet gives:   Unable to detect the URI-scheme of "trash:"

I'm a newbie... I did as much researchas I could but I hit a dead end.
 

I looked through the source on the awngarbage applet  and it seems that the applet calls  _xdg-open trash:_  when you clickthe icon. I don't know enough to attempt to change it. I included the code section below.


So I did some tests.


I have discovered that on 12.04 if Itype   _trash:_  into the location bar in Thunar it redirects to_   trash:///_   and opens the trash folder.  However, if I type the same _trash:_ into the 13.03 system nothing happens.  I get the exact same behaviorif I do _xdg-open trash:_  12.04 opens Thunar to the trash. On 13.04 _xdg-open trash:_  gets the  Unable to detect the URI-scheme of "trash:"response.


For the record if I enter   _trash:/_   into either system it redirects to    _trash:///_ and opens the trashon Thunar. 


If I enter  _gvfs-open trash:_  OR    _gvfs-open trash:///_  on either system Thunar is opened to the trash.


Is there a way to link make a link from  _trash:_  to _trash:///_  that should solve the issue ??



recap of my systems 
on 12.04 with AWN it is working asexpected
on 13.04 it is not working 
both systems are using the samepackages of awn and their required dependencies
avant-window-navigator0.4.1~bzr830-2ubuntu1
awn-applet-garbage 0.4.1~1507-0ubuntu7


section of awn-garbage-applet code:


case 1: /* left mouse click */
        try
        {
          string[] argv = new string[]{ "xdg-open", "trash:" };
          spawn_on_screen(this.get_screen (),
                           null,
                           argv,
                           null,
                          SpawnFlags.SEARCH_PATH,
                           null,
                           null);
        }

---

### Post by afredco on 2013-11-26
Found a fix
it is related to this - did the quick fix and now awn is working also magnet links are also fixed now![URL="https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/1173727"]
https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/1173727[/URL]

---

