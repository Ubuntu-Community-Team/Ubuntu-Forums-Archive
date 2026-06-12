---
title: "gdesklets +font size"
date: 2005-04-01
forum: General Help
---

### Post by cricque on 2005-04-01
I got gdesklets running on latest version with all updates, installed it with apt-get.

Everything works fine, just the font Size in SideStripes will not change ? anyone got an idea whats the problem perhaps with it ?

---

### Post by Buffalo Soldier on 2005-04-03
You're not alone. Having the same problem here.

EDIT:
I guess the developer already knows about this. [http://gdesklets.gnomedesktop.org/wish.php?func=gd_show_wish&gd_wish_id=396&gd_app_id=232](http://gdesklets.gnomedesktop.org/wish.php?func=gd_show_wish&gd_wish_id=396&gd_app_id=232)
> 
**Request from jeremec:**
It seems that, when using a self-installed SideStripes 0.3 and before, combined with the Debian 'unstable' gdesklets package, I am not able to set the font sizes using the configuration menu. Instead, the font sizes only change in proportion to the size of the desklet, and are insanely huge to begin with. Other desklet suites do not exude the same behavior. I am willing to help debug if necessary.

**Developer Response:**
Sorry, but it's clearly stated in SideStripes description: "text [...] scales automatically". What desklet size do you use if you consider fonts to be "insanely huge"? This may really require fixing, so drop me an email if you can.

---

### Post by ubunciak on 2005-09-02
something new in this case?

i have this same problem. what i can do? compile from sources?

---

### Post by uglysmurf on 2005-09-08
Modifying the python script and gdesklet XML display file to allow you to control font size via preferences should be fairly trivial (my favorite expression from work).

Using [http://www.gdesklets.org/develbook/book.html](http://www.gdesklets.org/develbook/book.html) as my guide, I was able to modify the countdown gdesklet from SideStripes as such:

comment out the lines that set the font in countdown.py:
 ```

def setup_local():
    s = Dsp.icon.height.as_px()
    Dsp.icon.uri = "gfx/countdown/" + cf_c_icon + ".png"
    Dsp.line1.color = pcolor
    Dsp.line2.color = scolor
#    Dsp.line1.font = font_size(cf_font, int(0.4*s), "bold")
#    Dsp.line2.font = font_size(cf_font, int(0.25*s))
    Dsp.line2.value = "until %s"%cf_c_event
    show()

``` 

and add in functional font preferences under <prefs> in countdown.display:
```

                <font label="Font:" bind="Dsp.line1.font" />
                <font label="Font:" bind="Dsp.line2.font" />
<!--          <font label="Font:" bind="cf_font"/> -->

``` 

I haven't looked yet, but the rest should be very similar.  If I do them all and clean it up nice, I'll share it out somehow.   :)

---

