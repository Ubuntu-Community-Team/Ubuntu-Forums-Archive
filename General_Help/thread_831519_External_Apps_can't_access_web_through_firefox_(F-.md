---
title: "External Apps can't access web through firefox (F-spot/Banshee)"
date: 2008-06-16
forum: General Help
---

### Post by tabithaboof on 2008-06-16
I am trying to configure F-Spot to work with Flickr but whenever I try to authorise F-Spot to work with my account firefox loads a blank "www.U%.com not found" page. It also happens with Banshee trying to open a link via audioscrobbler. 

I tried editing the command I use to launch firefox by removing the "%U" and now when I try to access a page via Fspot/Banshee I just get a blank page. 

Help much appreciated.

---

### Post by sdennie on 2008-06-16
What happens if you change your firefox command in Preferred Applications to be:

```

firefox "%s"

```

---

### Post by iaculallad on 2008-06-16
Try to right-click on your Firefox icon launcher, select "Properties" and remove %u on **firefox %u** under the "Command".

---

