---
title: "Close, minimise and Restore buttons"
date: 2021-06-10
forum: General Help
---

### Post by meetdilip on 2021-06-10
Hello, I have some issues with the button colours regarding the close, minimise and restore for Firefox 89. I wonder where does the theme store these files ? What name does - close, minimise, restore buttons has in the theme folder ? Thanks.

---

### Post by &amp;KyT$0P# on 2021-06-10
Is Firefox controlling those buttons in your case (is Customize Toolbar..., "Title Bar" un-checked)?  If so you can use [Browser Toolbox]("https://developer.mozilla.org/en-US/docs/Tools/Browser_Toolbox") to find the answer yourself.

---

### Post by meetdilip on 2021-06-10
@halogen2 Thanks for the response. The buttons are visible while using Yaru, Adwaita and other themes. I am using Plata. So I think it is the theme that decides the colour of the symbols.

---

### Post by TheFu on 2021-06-10
Historically, window decorations are the responsibility of the WM, the Window Manager.  The correct answer will be extremely dependent on the WM being used and whether the Gnome team got there fingers into the client-side code to force the WM to lose that control.  I'm not seeing any difference in the decorations (title, buttons, borders, scrollbar) in Firefix or any other window on my system running fvwm as the ICCCM2 2.0 compliant window manager.

---

### Post by meetdilip on 2021-06-10
I have this issue only with the FF light theme because the button symbols are close to white. If I move to another theme, everything is working. That is why I thought the symbol can be defined through the theme.

---

### Post by TheFu on 2021-06-10
> **meetdilip said:**
> I have this issue only with the FF light theme because the button symbols are close to white. If I move to another theme, everything is working. That is why I thought the symbol can be defined through the theme.

Interesting.  When I change FF to the "dark theme", nothing changes related to the window decoration.  Perhaps I'm not understanding which buttons are difficult to see?  My window borders are cornflower blue for the active window and gray for inactive windows.  The buttons are in the upper left-hand and upper right-hand corners. Those are completely normal regardless of the theme.  I only look at the built-in 4-5 themes.

BTW, thanks for asking this question - I've switched to the dark theme. Nice contrast. Here's the upper right-hand corner.

[ATTACH=CONFIG]288639[/ATTACH]

---

### Post by Frogs Hair on 2021-06-10
Same problem on a plata/materai.  based theme, but no others so far. I just added a Firefox theme. I see the problem when trying to use a dark gtk theme combined with a the light Firefox theme.

---

### Post by meetdilip on 2021-06-10
I hope we will be able to find some workaround.

---

### Post by Frogs Hair on 2021-06-10
My work around was to install a theme from the extensions page. The before and after is in the screen shots.

---

### Post by meetdilip on 2021-06-11
You mean not using the Light theme ? I switched to dark and a colourful theme that came pre-built. Used Firefox Colours addon to create my own colour scheme. However, I like the default FF light theme a lot. I still do not see how to use Plata and the Light theme together. Thanks.

---

### Post by Frogs Hair on 2021-06-11
> **meetdilip said:**
> You mean not using the Light theme ? I switched to dark and a colourful theme that came pre-built. Used Firefox Colours addon to create my own colour scheme. However, I like the default FF light theme a lot. I still do not see how to use Plata and the Light theme together. Thanks.

I installed the following theme.


[https://addons.mozilla.org/en-US/firefox/addon/google-chrome-light/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search](https://addons.mozilla.org/en-US/firefox/addon/google-chrome-light/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)

---

### Post by dddman on 2021-06-11
Has this been mention?
[https://color.firefox.com/](https://color.firefox.com/)
good for tweaking parts of a theme

---

### Post by meetdilip on 2021-06-11
I switched from Plata. I think that is the best method until I find out where to change the button symbol colours. It is not hard, but I got used to a new theme I downloaded for testing and the Light theme issue is not in play.

> **dddman said:**
> Has this been mention?
[https://color.firefox.com/](https://color.firefox.com/)
good for tweaking parts of a theme

I have this. Thanks.

---

