---
title: "Wget question"
date: 2008-02-21
forum: General Help
---

### Post by poet_will on 2008-02-21
Howdy.  I am trying to use wget to download the jpgs at this website:

[http://en.wikipedia.org/wiki/William-Adolphe_Bouguereau#Gallery](http://en.wikipedia.org/wiki/William-Adolphe_Bouguereau#Gallery)

No, I don't want the small pictures on that page, i want the large pictures two links into that page.  I.e. if you click on one of those thumbnails you go to another html page.  If you click again on the picture it takes you to the full size picture.  That is the picture that I want.  I have tried this:

wget -r -l4 --no-parent -A.jpg [http://en.wikipedia.org/wiki/William-Adolphe_Bouguereau#Gallery](http://en.wikipedia.org/wiki/William-Adolphe_Bouguereau#Gallery)

but it isn't pulling down anything.  Can someone help me out here?

Thanks

Will

---

