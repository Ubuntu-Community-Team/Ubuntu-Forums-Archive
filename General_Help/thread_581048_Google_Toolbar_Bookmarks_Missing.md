---
title: "Google Toolbar Bookmarks Missing"
date: 2007-10-19
forum: General Help
---

### Post by mahousaru on 2007-10-19
Using Ubuntu 7.10 (32 bit) with stock FF 2.0.0.6 and Google Toolbar 3.0.20070525L, and the Bookmarks button constantly says downloading bookmarks.

Checked the error console and I have the following errors:

```

Error: this.getTabBrowser() has no properties
Source File: file:///home/user/.mozilla/firefox/otgawp2j.default/extensions/%7B3112ca9c-de6d-4884-a869-9855de68056c%7D/lib/toolbar.js
Line: 474

Error: Cc['@google.com/toolbar/bookmark-wrapper;1'] has no properties
Source File: file:///home/user/.mozilla/firefox/otgawp2j.default/extensions/%7B3112ca9c-de6d-4884-a869-9855de68056c%7D/lib/toolbar.js
Line: 150

```

I noticed that my FF hangs ever so often whilst loading pages, and I narrowed it down to the toolbar as it does not hang with it un-installed.

I tried a fresh profile with a newly installed toolbar and I get the same thing.  

Thanks for you time!

---

### Post by andre2p on 2007-10-19
Same problem here after fresh install.:(

---

### Post by mahousaru on 2007-10-19
I've been hunting on the interweb and all I have found is people saying that there are problems with running it in a 64 bit OS.  There is one useful thread in regards to the libstdc++.so.5 req and gutsy has .6...  I guess its something thing to log with the google toolbar team.

[http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/920f5cd43515dfd0](http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/920f5cd43515dfd0)

---

### Post by kr0n1x on 2007-10-21
i've the same problem, and i've installed libstdc++5 (this have installed automaticcally gcc3 or similar package..)

but i have not solved the problem...

how to do? :<

thx bb ps: sorry my english.-.

---

### Post by devi99 on 2007-10-21
Yep same thing here. Same config Gutsy Gibbon as well. There must be some conflict somewhere.

---

### Post by Fran89 on 2007-10-21
Same thing here 7.10 Beta

---

### Post by Fran89 on 2007-10-21
hey i managed to make it work you have to install the libstdc++5 from synaptic package manager and anything else that comes with it (auto added)...  it works

---

### Post by mahousaru on 2007-10-21
> **Fran89 said:**
> hey i managed to make it work you have to install the libstdc++5 from synaptic package manager and anything else that comes with it (auto added)...  it works

Many thanks, that sorted out the problem for me too :)

I've seen other people say that it doesn't work for them.  They might need to restart firefox or disable googe toolbar and then re-enable it (with restarts).

---

### Post by vhof on 2007-10-22
Hmm.. Didn't solve for me.
BUT, I rebooted - don't know if it was needed, because it didn't help.
Then I went to toolbar.google.com and installed the toolbar again (didn't remove the previous one).
Now it works.

---

### Post by PiR2 on 2007-10-22
Same for me.  That is, I installed the missing package, but still no bookmarks.  Next, I rebooted, but still no bookmarks.  Then, I disabled and re-enabled the toolbar, but still nothing.  Finally, I reinstalled the Google Toolbar and all is well.

Thanks to all for your help!

---

### Post by kr0n1x on 2007-10-22
i haven't solved the problem trying all these solutions you wrote :(

---

### Post by jgonzalezo0501 on 2007-10-22
Yeah, me too

---

### Post by pertain on 2007-10-22
> **jgonzalezo0501 said:**
> Yeah, me too


I am facing the same issue!

---

### Post by justtech on 2007-10-22
I was facing the same issue until about 2:00 today.  I reinstalled the Google Toolbar and everything worked fine.  Of coarse I chased all the other ideas trying to get it to work first but that was the last thing I did before it worked.

---

### Post by JunSeok Kang on 2007-11-11
Same problem, solved without reinstalling the toolbar. 
Just installed libstdc++5 at Synaptic, and then 
disabled, restarted firefox, 
enabled, restarted firefox.
and it works!

Thanks!:)

---

### Post by kr0n1x on 2007-11-12
> **JunSeok Kang said:**
> Same problem, solved without reinstalling the toolbar. 
Just installed libstdc++5 at Synaptic, and then 
disabled, restarted firefox, 
enabled, restarted firefox.
and it works!

Thanks!:)

tried...not worked.
anyway i've 64 bit version of ubuntu... you?

a good alternative for have your bookmarks everywhere is to use del.icio.us service...with his two buttons.

[http://del.icio.us/](http://del.icio.us/)

---

### Post by kr0n1x on 2007-11-12
i found also this solution (works on my Gutsy 64 bit):

[https://addons.mozilla.org/en-US/firefox/addon/2448](https://addons.mozilla.org/en-US/firefox/addon/2448)

is a good Firefox addon, for your Google Bookmarks :) 

works well on my gutsy 64 bit

---

### Post by travnewmatic on 2007-11-28
thanks so much
worked like a charm

---

### Post by covertdlk1 on 2007-11-29
My bookmarks finally work!:KS!:KS!  I tried everything with no luck - synaptic packages, add-ons, and voodoo dolls.  Finally the tip that fixed it was to reload google toolbar right over the existing setup.  When reloaded, I signed out of google toolbar, restarted Firefox, signed back into google toolbar, and WHAM - my bookmarks are back!:KS!:KS!

---

### Post by antelopepoop on 2008-02-20
> **JunSeok Kang said:**
> Same problem, solved without reinstalling the toolbar. 
Just installed libstdc++5 at Synaptic, and then 
disabled, restarted firefox, 
enabled, restarted firefox.
and it works!

Thanks!:)

Woohoo!  This worked perfectly for me.  Note: I signed out before disabling.

I didn't have any luck with the fresh install of the toolbar over the old one.

I am running 
Gutsy + Adblock

---

### Post by jamaas on 2008-02-21
My problem is similar ... if I bookmark a page and add it to a folder on the bookmark toolbar it does not show up in the folder.  It is there if I hit Ctrl B and get the bookmarks on the sidebar, but will not show up in the folder at the top.  Can anyone tell me if this is the same or a different problem?

Thanks

Jim

---

### Post by ashishbond on 2008-07-05
My problem is still not solved. i tried almost everything suggested in this thread: synaptic / enable/disable/reinstall/signout then reinstall/what not
other than restarting my comp which i am going to do now.
please suggest how to bring my google bookmarks in the toolbar????
:confused:

---

