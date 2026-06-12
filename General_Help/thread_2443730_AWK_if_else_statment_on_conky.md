---
title: "AWK if else statment on conky"
date: 2020-05-19
forum: General Help
---

### Post by UpSignal on 2020-05-19
Hi there guys!

Since ubuntu 20.04 brings us Gamemode included, why not make conky work for us?
So, i added this to my conky: 

```
${exec gamemoded -s |awk '{print $3}' }
```

Final result, it will print "active" or "inactive" on my setup. Now, i want to bring this to the next level! Instead of printing the word itself, i want it to print ON or OFF accordingly.
I have no experience in scripting, i'm still learning, and i'm not getting the if statment to work!

I tried this:

```
gamemoded -s |awk 'if($3 =="active")' print "On" else 'if($3 =="inactive")' print "off"

```

However its not working :s. can anyone help?

---

### Post by VMC on 2020-05-19
I tested your awk statement:
```
$ echo on;awk 'if($3 =="active")' print "On" else 'if($3 =="inactive")' print "off"
on
awk: cmd. line:1: if($3 =="active")
awk: cmd. line:1: ^ syntax error
```

Mine:
```
$ echo on;awk '{if($3 =="active") print "On"; else if($3 =="inactive") print "off"}'
on
```

Appears missing "{}" blocks

---

### Post by UpSignal on 2020-05-19
Hi! thanks for your help!
Indeed it works, however it disables too the other lines bellow for my conky setup. i wonder why?

```
${color2}Game Mode:${color} ${alignr}${exec gamemoded -s |awk '{if($3 =="active") print "On"; else if($3 =="inactive") print "off"}'
```

Edit: all working! thanks!!

---

### Post by UpSignal on 2020-05-19
Heym can i ask just one more question?
in that line of code, how can i change the color of each print ? 

i'm trying to change the "off" color, but it doesnt work. tried the code before the print and after the print, no joy.

```
${color2}Game Mode:${color} ${alignr}${exec gamemoded -s |awk '{if($3 =="active") print "On"; else if($3 =="inactive") print ${color5} "off"}'
```

---

### Post by CatKiller on 2020-05-19
> **UpSignal said:**
> Heym can i ask just one more question?
in that line of code, how can i change the color of each print ? 

For this specific case, you can move things around  "if [exec awk blah] = active [color blah] else [other color blah]"

The way I do it is to shunt the conditional stuff into a lua script (I use them for colouring temperatures and fan speeds). I'll dig it out next time I'm near my computer if you're interested.

---

### Post by UpSignal on 2020-05-19
Sure, i would love too!
i'll try to figure it out, thanks man

---

### Post by CatKiller on 2020-05-19
So the way conky works with lua is that you need to declare your lua script in the conky configuration file, and I keep my conky scripts in the amazingly creatively-named ~/.conky/scripts, so my conky has a line in the header section that says

```
    lua_load = '~/.conky/scripts/conky.lua',
```

and in my conky lua script (called conky.lua) there's a function called conky_context_colour that takes an expression, three colours, and two numerical values as arguments, and returns the results of the expression coloured based on its value relative to those other values. So, for example, I can call ```
${lua_parse context_colour ${hwmon 2 temp 1} ${color4} ${color2} ${color3} 45 75}${color}°C
``` to display my CPU temperature as one colour if it's less than 45°C, another colour if it's more than 75°C, and a third if it's between them. I use the color*n* entries in the header section, but I could have different colours for each call of context_colour if I wanted.

The first part of conky.lua is a boilerplate section. I don't really understand exactly what it does, but it's
```
require 'cairo'

function conky_main()
if conky_window == nil then return end
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    cr = cairo_create(cs)
    cairo_set_antialias(cr, CAIRO_ANTIALIAS_NONE)
    local updates=tonumber(conky_parse('${updates}'))
    if updates>5 then

    end-- if updates>5
    cairo_destroy(cr)
    cairo_surface_destroy(cs)
    cr=nil
end-- end main function
```

The actual context_colour function is

```
function conky_context_colour(    expression,
                colour1,
                colour2,
                colour3,
                low_value,
                high_value)
    local foo=conky_parse(expression)
    local bar=tonumber(foo)
    if bar < tonumber(low_value)
        then colour=colour1
        else
        if bar > tonumber(high_value)
            then colour=colour3
            else colour=colour2
        end
    end
return colour..foo
end
```

I have that function in a lua script rather than doing it in conky because I didn't want to have to keep evaluating the expression over and over, and the nested ifs make the conky config really hard to read. You might notice that the function call from conky names the function context_colour, but in the script it's named conky_context_colour. I can't remember why that is, but it needs to be like that for some reason.

Obviously this function is dealing with numerical values (you can see that I'm using tonumber() to make sure it's a number before I compare the values) but you can amend it to compare strings. Having already used a script for all the temperatures and fan speeds, I then had somewhere to put other random functions that do similar things, so the displayed information about the mpd that's running on my raspberry pi stereo gets a different image if it's playing or paused, and my laptop shows the signal strength of its WiFi graphically. It's all quite fun once you get started.

---

### Post by UpSignal on 2020-05-20
Hi there!

Thanks a lot for sharing your configs, no doubt i have much to learn from there. the only experience i have with scripting is from changing values and watch what happens, and search google for codes and try to find their meaning, so its hard for me. 
I'm going to spend all day trying to figure out how to make that work with my code. 
If i get it to work, i'll come here :)
cheers

---

### Post by UpSignal on 2020-05-20
Ah.. i think i'll have to pass this one. It's just too hard for my skills (no skills :p).
The lua file is too much for me to handle. I also tried changing my command around, starting with the if condition, but just made a giant mess. I was trying to set a green colored "ON" when the result from |awk '{if($3 =="active"), and set the default color "OFF" when the result is inactive. Well, thanks anyway guys

---

### Post by CatKiller on 2020-05-20
> **UpSignal said:**
> the only experience i have with scripting is from changing values and watch what happens, and search google for codes and try to find their meaning, so its hard for me.

I mean, that's how I did it, too.

> **UpSignal said:**
> Ah.. i think i'll have to pass this one. It's just too hard for my skills (no skills :p).
The lua file is too much for me to handle.

There are accessible guides around for lua scripting specifically with conky. It was a *long* time ago that I set this up, so I couldn't tell you what I read at the time. Maybe an example that compares text strings would help?

```
function conky_mpd_image(    image1,
                image2,
                image3,
                positionx,
                positiony)
    local status=conky_parse('${mpd_status}')
    if status == "Playing"
        then picture=image1
        else
        if status == "Paused"
            then picture=image2
            else picture=image3
        end
    end
    output="${image ~/.conky/images/"..picture.." -p "..positionx..","..positiony.."}"
return output
end
```

> I also tried changing my command around, starting with the if condition, but just made a giant mess. I was trying to set a green colored "ON" when the result from |awk '{if($3 =="active"), and set the default color "OFF" when the result is inactive. Well, thanks anyway guys

I don't have any conky configurations with ifs in any more to crib from (because they got put in lua instead), but conky can do *if* and *else* on its own. You can see all the functions [here](http://conky.sourceforge.net/variables.html). So you could do something like

```
${if_match "${exec gamemoded -s | awk '{print $3;}'}" = "active"}${color5}ON${color}${else}OFF${endif}
```

I haven't tested it, so there may be something up with it as written, but that's the kind of thing.

---

### Post by UpSignal on 2020-05-22
Hi!

Sorry for the delay! thanks for helping me, your command works for the color part, but it's always printing ON, no matter the condition.
as the condition says "inactive" when doing gamemoded -s , it should print off

---

### Post by CatKiller on 2020-05-22
Well, like I said, I didn't test it. It's possible you need == rather than =. It's been a while. Or there might be some other syntax thing.

---

### Post by UpSignal on 2020-05-22
Holy shh!! you're right!! == did it!
thanks a bunch man... really appreciate it!
sooner or later something else will come up that i'll need to add. So i guess learning to mess with the LUA files is really a need.
Cheers man

---

