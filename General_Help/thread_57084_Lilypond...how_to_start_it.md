---
title: "Lilypond...how to start it?"
date: 2005-08-15
forum: General Help
---

### Post by lucaflea on 2005-08-15
hi. i don't have direct access to the net so i have to download all the .deb packages i need (with their dependencies....) and manually install them.
so it was for lilypond.....
i thought i installed everything but when i type "lilypond" in a terminal it returns me a list of "-- something" to type but none of them tells me how to start the program...
how can i get it work? i just want a linux version of finale/sibelius....


another question: why are my audio and video out of sync when running a divx/xvid with totem? i hope someone helps me...

luca ](*,)

---

### Post by charlieg on 2005-08-15
Attached is a screenshot of when I mark Lilypond for installation in Synaptic.

---

### Post by charlieg on 2005-08-15
Another good resource for help would be the user mail list for Lilypond:
[http://lists.gnu.org/mailman/listinfo/lilypond-user](http://lists.gnu.org/mailman/listinfo/lilypond-user)

---

### Post by lucaflea on 2005-08-15
it seem i have all the files i need but...what to type?

---

### Post by lucaflea on 2005-08-16
someone can help me????

it seems i have all installed but if in a terminal i write "lilypond" it says i have to type: "lilypond [OPTIONS] file"

what does it mean?


luca

---

### Post by jeremytaylor on 2005-08-16
From what i understand of lilypond it's kindof like tex in that you write a file in the lilypond markup (with whatever your favourite text editor is) then process it with lilypond.  Their website even has a crash course on how to use it and some demo files for you to try at [http://www.lilypond.org/web/switch/howto](http://www.lilypond.org/web/switch/howto)
hope that helps
Jeremy

---

### Post by charlieg on 2005-08-16
Yeah, it may not be the type of editor you are looking for, which is a shame.

There is Rosegarden, which may be better suited to your needs:
[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by lucaflea on 2005-08-16
thanx guys. it was enlightening!

i already installed rosegarden but when i launch it it takes a lot to start and some errors occur. it says that there are problems with midi...

is there a right way to config jack/alsa?

luca

---

### Post by charlieg on 2005-08-17
Search is your friend.  Took me <5s to find this:
[http://ubuntuforums.org/showthread.php?t=30963&highlight=midi](http://ubuntuforums.org/showthread.php?t=30963&highlight=midi)

---

### Post by dawynn on 2005-08-28
Having (briefly) tried some of the other engraving products out there, and always coming back to lilypond, I'd like to give my two-cents worth.

First, understand that Lilypond is just a command-driven tool.  They have no intention of ever building a GUI frontend.  Having said that, there is another group that has built "denemo" which is another package you can install, that will provide somewhat of a frontend and will build lilypond files for you.

Second, you should be aware that Ubunutu is WAY behind the times as far as Lilypond is concerned.  If you have a question, and want to start asking the community, you may not want to be running a version that's two generations obsolete (Lilypond is currently in the 2.6 series.  Debian uses a version in the 2.4 series.  For some reason, Ubuntu (even Breezy) uses a version in the 2.2 series).  Fortunately, the Lilypond folks ([www.lilypond.org](www.lilypond.org)) have gone the autopackage way -- meaning that even if your distribution of Linux does not have the latest version, you can still be up-to-date.

Third, denemo has not kept up with the times (they're also stuck in 2.2), but Lilypond has a wonderful little conversion tool (convert-ly) that can bring your files up-to-date.  This conversion tool is also helpful if you've written music in the obsolete 2.2 format, and want to move to the latest version of Lilypond.

Lilypond does have fantastic documentation (too bad the documentation doesn't come in an autopackage format).  And they do have a help email address (although it can take a few days to get a response).  It is definitely worth taking a look at, if you're willing to spend a bit of time learning the syntax.

 -- David

---

