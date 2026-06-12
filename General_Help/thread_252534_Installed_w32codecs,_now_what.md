---
title: "Installed w32codecs, now what?"
date: 2006-09-06
forum: General Help
---

### Post by marianom on 2006-09-06
There's this radio program I can only listen in internet. Unlucky for me it's embed in a web page and after accessing the page info, I discovered it's a application/x-mplayer2 object.

So I installed the w32codecs as seen @ [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

But know I fail to see how to continue and finally listen to my program.

Anyone can guide me in order to accomplish this?

As always, thanks a lot.

---

### Post by croak77 on 2006-09-07
You'll want the mozilla-mplayer plugin. It's in multiverse. If you don't know how to manage repo's, there is a links at the begining of that page you posted.

---

### Post by mssever on 2006-09-07
If croak's suggestion doesn't work, you can try this:

View the source of the page in question and determine the actual URL of the media file. Paste that into a media player such as Real Player.

---

### Post by marianom on 2006-09-07
Thanks for your answers.
I was hoping to use Rhythmbox but it does not work (no error message either).

I tried with Real Player too with no luck. I couldn't find wmplayer listed in the availables plugin so that's the reason, I guess.
Do you guys know how can I update it?

I will try now with mozilla-mplayer plugin. I will take a look in the repository for it.

---

### Post by mssever on 2006-09-07
What format is the file you're trying to play? WMA?

I use the version of Real Player from Automatix--along with all the codecs that Automatix has. So far, it plays everything I've come across.

---

### Post by marianom on 2006-09-07
As far as I can see it says application/x-mplayer2 and the link is [http://audio.grupolatinoderadio.com/envivo.ASX?EMI=ARCON](http://audio.grupolatinoderadio.com/envivo.ASX?EMI=ARCON) (this is the only embed link I get from the source page) and in the properties tab it says:
*Windows Media Audio 9.1 16 kbps, 22 kHz, mono 1-pass CBR*

---

### Post by mssever on 2006-09-08
I pulled up that link in Firefox and looked at the source, where I found the *real* URL: [http://66.175.96.10/arcontinental](http://66.175.96.10/arcontinental). However, I haven't had any success playing this, either. MPlayer played it for a fraction of a second, but then crashed. Here are a couple of Wikipedia links: 
[LIST]
[*][http://en.wikipedia.org/wiki/Advanced_Stream_Redirector](http://en.wikipedia.org/wiki/Advanced_Stream_Redirector)
[*][http://en.wikipedia.org/wiki/Advanced_Systems_Format](http://en.wikipedia.org/wiki/Advanced_Systems_Format)[/LIST]Because of the proprietary nature of the format, it might not be possible to play this stream in standard Linux software. There probably exists non-free Linux software that can do this (Linspire's stuff comes to mind), but I don't know any to recommend. You can thank Microsoft for this situation.

---

### Post by marianom on 2006-09-08
You can be sure: I was already thanking ms for this...

Anyway, thank you (this is for real) for the followup.

I will check those links and see where I end.

---

