---
title: "Compton's opacity rule"
date: 2014-10-28
forum: General Help
---

### Post by vasa1 on 2014-10-28
In this sample compton.conf (from [https://github.com/chjj/compton/blob/master/compton.sample.conf](https://github.com/chjj/compton/blob/master/compton.sample.conf)), there is line #43 which has this content:```
# opacity-rule = [ "80:class_g = 'URxvt'" ];
```Can someone please explain what this line does when uncommented? Does it set an opacity of 80% for windows of URxvt? But then what is **:class_g**? And how can I make an opacity-rule for any other program's window? I'd specifically like to have this rule for Google Chrome.

compton --help says that compton-trans is better than opacity-rule. But I didn't understand the man page for compton-trans :(

---

### Post by jhay2 on 2014-10-28
i don't like compton .. it makes my browser slow , and lag from window resizing and uses much ram  

xcompmgr on the other hand has no problem on my browser and very lightweight but it makes my opengl games run slow -_-


just sharing my thoughts sorry for this .. :) 

i dont know much of compton  so im waiting some expert on compton so i just drop by here ;)

---

### Post by mcduck on 2014-10-28
You pretty much got it right, the "80" means 80% opacity, and the rest is the rule for which windows the setting should be applied. There are various ways how a specific window can be defined in the rule, you can use class, type, ID or name (probably some others as well but I really can't remember them).

For example "name" would be what you see in a window's titlebar, so if you can be sure the name is always going to be the same, this is the easiest way to apply settings to a specific application window. "ID can be useful for multiple windows from the same application, or when the name might change.

Window class and window type are more generic rules that allow you to configure multiple applications, for example type of "Normal" would match all normal application windows, but probably not panels, popups, menus etc. And similarly, type "popup" would apply to popup messages and menus.

I'm sure there's some decent document about various window types, classes etc. X uses, but you can also run "xwininfo -all" in a terminal and then click any window to get all the window's properties.

It's been a while since I've played around with my compton settings, and even longer since I stopped using xcompmgr, but in general Compton is the better one with less bugs and more features. However some of it's features will make things really slow if you don't have graphics hardware that supports it (and also make sure compton is set to use hardware compositing). xcompmgr is the "safer" choice as the simpler options it has don't include anything that would make things really slow if you only have software rendering available. Since compton is pretty much a fork of xcompmgr, assuming you nsue same settings on both you should get more or less the same performance.

---

### Post by vasa1 on 2014-10-28
@mcduck, thanks for replying :) I got some experience of window nomenclature because Openbox allows window-specific rules pretty much like what you describe and I've used *xprop* to get their handles.

I've also used *wmctrl -l* and *wmctrl -lx* a bit. It's the "syntax" in the line I mentioned that got me confused. But I think I've got what I want.

Here is my ~/.config/compton.conf:```
# Opacity
menu-opacity = 0.8;
inactive-opacity = 0.8;
frame-opacity = 0.7;
inactive-opacity-override = false;

#WORKS
opacity-rule = [ "85:name *= 'Chrome'"];
```The reason I wanted to get an opacity rule for Google Chrome is to lessen the "whiteness" of the screen without resorting to stylesheets or the [High Contrast extension]("https://chrome.google.com/webstore/detail/high-contrast/djcfdncoelnlbldjfhinnjlhdjlikmph?hl=en-US").

Edit: just to put a value to it, with an opacity of 85 what is #ffffff in a Chrome page appears to be #d8d8d9 (according to gcolor2). Using 80, gets me #d1d0cf.

Edit 2: @mcduck, re. your edit, I keep a constant watch on %CPU usage and temp (and RAM) because I don't want my laptop to overheat. So I'll be careful.

Edit 3: that opacity-rule affects the xombrero browser as well. So that rule needs to be made more specific.

---

### Post by mcduck on 2014-10-28
yeah, I agree, the old-style conditions are bit confusing. There seems to be a bit easier and more flexible way of defining things available: [https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions]("https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions")

I like the idea of using compton to get rid of to bright backgrounds on web pages, I used to do something similar with Compiz, but haven't checked if Compton has any more direct way of doing it than just the opacity. If nothing else, then the option to render with  custom OpenGL fragment shader would of course work (at least as long as you are using the GL backend). Luckily there seems to be example shaders included, and they are pretty simple so modifying one to darken everything a bit (or anyhting above certain brightness) should be pretty easy and would probably look a bit cleaner than using transparency does...

---

### Post by vasa1 on 2014-10-28
> **mcduck said:**
> yeah, I agree, the old-style conditions are bit confusing. There seems to be a bit easier and more flexible way of defining things available: [https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions]("https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions")Thanks for the link :)

> **mcduck said:**
> I like the idea of using compton to get rid of to bright backgrounds on web pages, I used to do something similar with Compiz, but haven't checked if Compton has any more direct way of doing it than just the opacity. If nothing else, then the option to render with  custom OpenGL fragment shader would of course work (at least as long as you are using the GL backend). Luckily there seems to be example shaders included, and they are pretty simple so modifying one to darken everything a bit (or anyhting above certain brightness) should be pretty easy and would probably look a bit cleaner than using transparency does...I've just started using Compton (and compositing) and have a lot to learn. At this stage I don't know how to find out whether I am or am not "using the GL backend". And yes, using a "shader", if that is possible, to reduce brightness would make more sense than using opacity. I got the opacity idea when I saw that the Chrome window dimmed when it wasn't in focus.

---

### Post by vasa1 on 2014-10-29
> **mcduck said:**
> ...

I'm sure there's some decent document about various window types, classes etc. X uses, but you can also run "xwininfo -all" in a terminal and then click any window to get all the window's properties.

...
I came across [LibreOffice tooltips do not follow wintype settings]("https://github.com/chjj/compton/issues/142") on how to hunt down information on tooltips. Awesome (in a scary way).

---

### Post by mcduck on 2014-10-30
> **vasa1 said:**
> Thanks for the link :)

I've just started using Compton (and compositing) and have a lot to learn. At this stage I don't know how to find out whether I am or am not "using the GL backend".

I'd assume Compton will use x renderer as the backend unless you tell it otherwise.

> 
 --backend BACKEND

    Specify the backend to use: xrender or glx. GLX (OpenGL) backend generally has much superior performance as far as you have a graphic card/chip and driver.


---

### Post by mcduck on 2014-10-30
I don't seem to have new enough Compton version to have the "--glx-fshader-win" option, but here's the shader code I was planning on testing:

```
uniform float opacity;
uniform bool invert_color;
uniform sampler2D tex;

void main() {
	vec4 c = texture2D(tex, gl_TexCoord[0]);
	if ((c.r > 0.8) && (c.g > 0.8) && (c.b > 0.8)) {
    	         vec3 cc = min(vec3(c.r, c.g, c.b), 0.8);
   		 c = vec4(cc, c.a);
        }
	if (invert_color)
		c = vec4(vec3(c.a, c.a, c.a) - vec3(c), c.a);
	c *= opacity;
	gl_FragColor = c;
}
```

(there's definitely smoother ways to limit the brightness but just simply clamping it seemed like a decent start. Don't know it it works or not, though, I've only ever written CG and OSL shaders, an like I said, I couldn't test this one myself...)

---

