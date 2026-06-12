---
title: "Gaim plugins"
date: 2005-08-02
forum: General Help
---

### Post by manobes on 2005-08-02
Hi,

I'm trying to install the gaim-latex plugin, which can be found here
[http://sourceforge.net/projects/gaim-latex](http://sourceforge.net/projects/gaim-latex).

It compiles fine, and I have the required dependancies (tex2im and imagemagick).  Yet when I install the plugin in ~/.gaim/plugins it doesn't show up.  I've also tried putting it in with all the other gaim plugins, it still won't show up in tools - plugins

Any gaim experts out there?

---

### Post by kassetra on 2005-08-03
[QUOTE=manobes]Hi,

I'm trying to install the gaim-latex plugin, which can be found here
[http://sourceforge.net/projects/gaim-latex]("http://sourceforge.net/projects/gaim-latex").

It compiles fine, and I have the required dependancies (tex2im and imagemagick). Yet when I install the plugin in ~/.gaim/plugins it doesn't show up. I've also tried putting it in with all the other gaim plugins, it still won't show up in tools - plugins

Any gaim experts out there?[/QUOTE]

What version of gaim are you using?  On my system I get to my plugins list with Tools->Preferences->Plugins, or right clicking on the icon in my notify area and then left clicking on Preferences and then Plugins.  Then I have to checkmark the "Load" option next to each of the plugins I want to use and restart gaim.

You have tetex-base, tetex-bin, tetex-extra installed also, right?

Have you checked the permissions on the plugin file?  Do you have sufficient permissions to use it?

---

### Post by manobes on 2005-08-03
[QUOTE=kassetra]What version of gaim are you using?  On my system I get to my plugins list with Tools->Preferences->Plugins, or right clicking on the icon in my notify area and then left clicking on Preferences and then Plugins.  Then I have to checkmark the "Load" option next to each of the plugins I want to use and restart gaim.

You have tetex-base, tetex-bin, tetex-extra installed also, right?

Have you checked the permissions on the plugin file?  Do you have sufficient permissions to use it?[/QUOTE]

Yes, the problem is that it doesn't show up in the plugins menu.  I see all the other default plugins (like gaim-encryption) but there's no latex plugin.  I have adjusted the permissions, a+rwx, nothing.

I have a working TeX setup.

As a stop-gap, I installed kopete.  Its latex plugin works as advertised.

---

