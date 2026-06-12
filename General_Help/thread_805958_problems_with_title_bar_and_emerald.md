---
title: "problems with title bar and emerald"
date: 2008-05-24
forum: General Help
---

### Post by eskay_karthik on 2008-05-24
Till today, I have not tried anything in visualizations. 
I installed a new Ubuntu Studio theme. Then, I installed compiz-fusion and turned on a few features. All are working fine except that the title bar is missing. When I go to System->Preferences->Appearance, I have the following problems...
When I set the visual effects settings to Extra, I can see the title bar, but it is transparent(only the application or the window name is seen), and also in some other theme, I donno which. 
When I set it to None, the title bar theme changes back to the Ubuntu Studio theme I installed. 
When I select Custom after this, the title bar of unknown theme remains....
Please help me. I also find Emerald Theme Manager in System->Preferences. But I am unable to uninstall it, using Add or remove progs ...

Pls help
eskay

---

### Post by Forlong on 2008-05-24
Try running this in a terminal when Compiz is running:
```
gtk-window-decorator --replace &
```

---

