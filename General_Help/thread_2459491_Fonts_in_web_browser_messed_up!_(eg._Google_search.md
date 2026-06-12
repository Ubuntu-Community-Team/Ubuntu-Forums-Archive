---
title: "Fonts in web browser messed up! (eg. Google search)"
date: 2021-03-19
forum: General Help
---

### Post by Brent_Santin on 2021-03-19
In a [previous thread]("https://ubuntuforums.org/showthread.php?t=2459394") I asked about how to migrate fonts from an older Lubuntu computer to a new one.  After moving the font files to the new computer, It was advised that I do "sudo fc-cache -fv" to make the system aware of the newly migrated fonts. I think this messed up something for Firefox, the web-browser I use in Lubuntu. Now, many websites have a strange **bold font** substituted for what would have been their normal font.  This is most apparent in Google search results, which are almost all in bold, but I've seen it other places too, like in e-mails in Office 365's Outlook application, and the very text box into which I'm typing this message (only the text I'm entering in the text box appears wrong, the text in already posted on other threads looks normal). The "wrong" font looks like "Arial Bold". (Edit: once I posted this message and looked at it, the posted message used the "normal" font for this forum).

I've attached several screenshots to illustrate the issue. These show two identical Google searches: one on the old computer (with the correct font we all know) and the other on my new computer (with the wrongly substituted font). Other search engines like Bing are also affected (does it use the same  system font?) while Duckduckgo.com is not (maybe it uses a different  font for its search results).

This started happening with a fresh installation of Lubuntu 20.04 shortly after I migrated my old fonts and did the fc-cache. The first time I noticed the problem I wiped the OS and re-installed it (which fixed the issue) but the bold font came back once I migrated the fonts over from my old computer again and ran fc-cache again. The only thing I can guess happened is that running fc-cache somehow  corrupted a commonly used browser font and Firefox is substituting a  fallback font.  Makes web browsing very annoying to look at and I'd love  to fix it!

Note: this doesn't appear to be an issue with Firefox's font settings. I went in there and made sure everything was correct, and that web-sites are set to use their own fonts.
If anyone can help it would really be appreciated![COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Please see attached pictures.[/COLOR]

---

### Post by CatKiller on 2021-03-19
> **Brent_Santin said:**
> The only thing I can guess happened is that running fc-cache somehow  corrupted a commonly used browser font and Firefox is substituting a  fallback font.

I would say that the exact opposite has happened. Before, you didn't have a font that matched "arial" so you got whatever your system matched to "sans-serif," which is the next-listed font. Maybe a Bitstream Vera or a DejaVu? Now you *do* have a font that matches "arial" even if it's the bold version, so that's what you get. I have no idea which fonts you've actually got, though, nor the internal substitutions you might be using.

---

### Post by Brent_Santin on 2021-03-19
But the font that was "correct" before the issue appeared (on my old computer and on my new fresh computer before it reared its head) was exactly the same font as I've seen on every other computer ever when using Google, etc.
I'll have a look through the fonts I newly installed and see if any of them match the "wrong" bold font that is appearing.

---

### Post by CatKiller on 2021-03-19
The Bitstream Vera, DejaVu, Liberation, whatever, fonts are metric-compatible with the Microsoft fonts, so they're the same size and broadly the same shape. You'd have to be quite a font nerd to spot the differences between them if you weren't looking for them.

I don't know what font you were using on your old computer that you don't have on your new one.

There is a way to see which font will be provided for a particular font request, but I can't remember what it is. I'm sure you'll be able to look it up, though.

---

### Post by Brent_Santin on 2021-03-19
I found the problem and you were right, CatKiller. I somehow installed a font that is conflicting with the online font Google (and other sites) are requesting. So the incorrect looking (local) font with the same name is substituted when rendering websites.
The "guilty" font is in my custom fonts folder:

/home/brent/.local/share/fonts/

...because if I rename this fonts folder to "fonts.disabled" and restart Firefox, everything looks normal again.

Using "Inspect Element" in Firefox I could see Google was requesting the Arial font for its text body. There were multiple versions of the Arial font in the folder referenced above. I removed them and renamed the folder back to just "fonts", started up Firefox, and everything looked fairly normal again. Well, you can see Google search results is using a default Lubuntu font that is very close to the light Arial font but it looks almost the same.

Since I like to have Arial (a very common font) on my computer for use in other software, I found free version online and did a re-install of it. This version of Arial works properly with Firefox/Google search results as well.

Thanks,

---

