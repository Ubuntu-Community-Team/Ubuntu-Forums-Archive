---
title: "Gutsy - cannot install printer konica minolta 2430DL"
date: 2007-11-27
forum: General Help
---

### Post by goneskiing on 2007-11-27
Who broke printing in Gutsy ?  Really stupid - I just missed a FedEx deadline.

This printer worked fine under Feisty - now with new Gutsy printing dialog I cannot even get the printer installed:

1) the 2430DL drivers no longer seem there
2) the new dialogs ask for a password but then won't take it
3) the printing options don't indicate things like color vs greyscale, etc
4) I get a cups error if I try to print.

any fixes ?  this is a showstopper !

---

### Post by Ashrael on 2007-12-04
Same problem here, it won take my passwd... tried changing it, to no avail....
Now I cannot print my Karaoke list :popcorn:

Some 's broken.

---

### Post by goneskiing on 2007-12-09
I got it fixed (found answer on web somewhere - it's a more generic problem with the new dialog and cups

[http://localhost:631/](http://localhost:631/)
sudo lppasswd -a <username> [cupspassword]
sudo gpasswd -a <username> lpadmin

---

