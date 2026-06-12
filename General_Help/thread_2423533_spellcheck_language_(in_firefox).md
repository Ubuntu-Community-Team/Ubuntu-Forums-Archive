---
title: "spellcheck language (in firefox)"
date: 2019-07-25
forum: General Help
---

### Post by Skaperen on 2019-07-25
i just realized that the spelling checker running on forms in firefox (such as entering this post) is using British English, but i want to be using American English (being located in West Virginia, USA).  Xfce has "English (United States)" already set, but in Firefox i get only 2 choices "English (Canada)" and "English (United Kingdom)".  i need "English (United States)" here, too.

here is some of [FONT=courier new]dpkg -l[/FONT] output that seems relevant.  Xubuntu has install languages i clearly don't need, but when text appears in languages i don't know, i still prefer it be formed in the display correctly.
```

ii  firefox-locale-en                     68.0+build3-0ubuntu0.18 amd64                   English language pack for Firefox
ii  fonts-beng-extra                      1.0-6ubuntu0.1          all                     TrueType fonts for Bengali language
ii  fonts-droid-fallback                  1:6.0.1r16-1.1          all                     handheld device font with extensive style and language support (fallback)
ii  fonts-guru-extra                      2.0-4ubuntu0.1          all                     Free fonts for Punjabi language
ii  fonts-indic                           2:1.2                   all                     Meta package to install all Indian language fonts
ii  fonts-kacst-one                       5.0+svn11846-9          all                     TrueType font designed for Arabic language
ii  fonts-khmeros-core                    5.0-7ubuntu1            all                     KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                             0.0.20060226-9ubuntu1   all                     TrueType font for Lao language
ii  fonts-pagul                           1.0-7                   all                     Free TrueType font for the Sourashtra language
ii  fonts-samyak-gujr                     1.2.2-4                 all                     Samyak TrueType font for Gujarati language
ii  fonts-samyak-mlym                     1.2.2-4                 all                     Samyak TrueType font for Malayalam language
ii  fonts-samyak-taml                     1.2.2-4                 all                     Samyak TrueType font for Tamil language
ii  gawk                                  1:4.1.4+dfsg-1build1    amd64                   GNU awk, a pattern scanning and processing language
ii  ghostscript                           9.26~dfsg+0-0ubuntu0.18 amd64                   interpreter for the PostScript language and for PDF
ii  ghostscript-x                         9.26~dfsg+0-0ubuntu0.18 amd64                   interpreter for the PostScript language and for PDF - X11 support
ii  iso-codes                             3.79-1                  all                     ISO language, territory, currency, script codes and their translations
ii  language-pack-en                      1:18.04+20180712        all                     translation updates for language English
ii  language-pack-en-base                 1:18.04+20180712        all                     translations for language English
ii  language-pack-gnome-en                1:18.04+20180712        all                     GNOME translation updates for language English
ii  language-pack-gnome-en-base           1:18.04+20180712        all                     GNOME translations for language English
ii  language-selector-common              0.188.3                 all                     Language selector for Ubuntu
ii  language-selector-gnome               0.188.3                 all                     Language selector for Ubuntu

```

---

### Post by speartip on 2019-07-25
Hit the Firefox Menu. Preferences. Language. In the drop down box, search for more languages. Select a language to add. The scroll down to English (United States) & hit the add button. If it doesn't set as default, move it to the top of the list, or delete the other languages.

---

### Post by Skaperen on 2019-07-25
it does not show "English (United States)" in Firefox.  it shows only "English (Canada)"  and "English (United Kingdom)".

---

### Post by tea for one on 2019-07-25
> **Skaperen said:**
> it does not show "English (United States)" in Firefox.  it shows only "English (Canada)"  and "English (United Kingdom)".

Firefox > Edit > Preferences > Language > Arrow Down  > Search for more languages > Select a language to add

---

### Post by Skaperen on 2019-07-25
i do that and nothing changes.

---

### Post by tea for one on 2019-07-25
> **Skaperen said:**
> i do that and nothing changes.

Can you be a bit more specific?

You select the English United States version?

The English United States is not in the drop down list?

After the language selection you have to hit **Add**

---

### Post by Skaperen on 2019-07-26
i do hit add and it tells me the changes will not take affect until i restart firefox.  i quit and restart and the change is gone.

---

### Post by tea for one on 2019-07-27
> **Skaperen said:**
> i do hit add and it tells me the changes will not take affect until i restart firefox.  i quit and restart and the change is gone.

I suspect that your Firefox profile has been affected/corrupted somehow. 

Nevertheless, I suggest that you have a look at the Mozilla support pages such as [https://support.mozilla.org/en-US/kb/how-to-fix-preferences-wont-save](https://support.mozilla.org/en-US/kb/how-to-fix-preferences-wont-save).

Hopefully, there may be a solution there.

---

### Post by Skaperen on 2019-07-27
i deleted the prefs file and started over.  it's working now, so, that was the problem.

---

### Post by tea for one on 2019-07-27
> **Skaperen said:**
> i deleted the prefs file and started over.  it's working now, so, that was the problem.

Just out of curiosity - have you been changing settings in the Firefox **about:config**?

Also, please mark the thread as solved to help all forum users/searchers.

---

### Post by Skaperen on 2019-07-27
> **tea for one said:**
> Just out of curiosity - have you been changing settings in the Firefox **about:config**?

not on this user's firefox.  i have on another user's firefox.

---

