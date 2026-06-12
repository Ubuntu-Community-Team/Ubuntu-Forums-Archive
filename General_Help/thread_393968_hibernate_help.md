---
title: "hibernate help"
date: 2007-03-26
forum: General Help
---

### Post by dangeresque on 2007-03-26
i am running ubuntu ultimate 1.3 on my laptop and i can't get the hibernate function to work properly. when i tell it to hibernate i just get a black screen with a blinking courser in the top left corner of the screen and then it goes to my screen saver. any help that you guys can give me would be nice.

thank you

---

### Post by greenex on 2007-03-28
i have the same problem.  i'm using the gamer's edition.  i get the black screen with the cursor but it never goes to a screensaver

---

### Post by kev000 on 2007-03-28
hibernate using swsusp isn't compatible with every piece of hardware.  Without knowing your specific hardware, you may have a module that isn't hibernate friendly.  My suggestion would be to download the hibernate scripts from [suspend2.net]("http://suspend2.net") and hack around with the conf files a bit.  You'll be able to unload and reload modules when you hibernate/resume so hibernate will actually work.

---

