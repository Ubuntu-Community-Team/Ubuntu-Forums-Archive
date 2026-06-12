---
title: "Document Viewer 3.10.3 permission denied when trying to open .pdf"
date: 2016-01-02
forum: General Help
---

### Post by jhboards on 2016-01-02
I burned some files to a CD to free us some space on my SSD. I tried opening several of the files on the CD to ensure the burn was successful. When I tried to open any of the .pdf files from the CD using Document Viewer 3.10.3, I received an error message stating I did not have permission to open the file. I checked the file permissions and even changed them to read only, but to no avail. The same files still on my PC would open, but the burned copies returned the "permission denied" message.

[Note: files without a .pdf extension opened OK off the SSD, but not the  CD, I don't know why, but this did fix the issue for me]
  
This is a problem with the Apparmor security profile in Document Viewer 3.10.3, in that, unless the file name ends in ".pdf", the evince package in Ubuntu 14.04 will return a "permission denied" message. 

Running the following from a terminal solved my problem:
> sudo apt-get install apparmor-utils
sudo aa-complain /usr/bin/evince

I keep my 14.04 updated on a weekly basis. Apparently, this update has not been pushed out.

The full description can be found here:

[http://www.mail-archive.com/search?l=desktop-packages@lists.launchpad.net&q=subject:%22](http://www.mail-archive.com/search?l=desktop-packages@lists.launchpad.net&q=subject:%22)[Desktop-packages]+[Bug+867749]+Re%3A+Permission+Denied+error+when+reading+a+pdf+format+file+whos+name+doesn%27t+end+in+.pdf%22&o=newest&f=1

---

