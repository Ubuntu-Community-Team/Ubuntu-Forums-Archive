---
title: "Drual and Wordpress simultaneous installation, one server?"
date: 2008-06-03
forum: General Help
---

### Post by BrendanM on 2008-06-03
So I have a development server with the LAMP stack installed, and Drupal on there. I would like to set up a wordpress installation to play with too, I understand there's some way to make Ubuntu/Apache2 serve two separate websites off the same box, accessible by different URLs, but I don't have the slightest clue of how to do that.

Could somebody take me through how to do this, keeping it as simple and basic as possible (and keeping in mind that I already have Drupal installed and working, and I'd like to not mess that up), or at least point me in the direction of helpful resources?

Thanks a lot.

---

### Post by EXCiD3 on 2008-06-03
I'm not sure exactly what you mean exactly but if you are wanting something like i currently have (trying out drupal) its fairly easy.

Here is my main site: [http://excid3.pcriot.com](http://excid3.pcriot.com) (wordpress)
and hidden away is my drupal installation that ive been toying around with: [http://excid3.pcriot.com/drupal](http://excid3.pcriot.com/drupal)

Now all you have to do is install drupal to a different folder inside your public html folder and setup a separate mysql database for it to use. then you can access the other installation by just adding a /<foldername> to the end of your site like the /drupal is on mine.

---

### Post by BrendanM on 2008-06-03
That sounds like it would work. Somebody told me I needed to do some crazy **** with like "virtual servers" on apache.

---

### Post by EXCiD3 on 2008-06-03
Well you would had you been trying to host two websites (as in domains like [www.example.com](www.example.com) and [www.example2.com](www.example2.com)) on the same server. Just hosting two different web apps is a completely different thing. Just install Wordpress like you did Drupal except use a separate database and throw your Wordpress install in a /wordpress (or /blog, etc) folder instead of extracting to the main web folder.

---

