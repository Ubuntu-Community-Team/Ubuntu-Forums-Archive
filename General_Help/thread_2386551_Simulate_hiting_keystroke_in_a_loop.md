---
title: "Simulate hiting keystroke in a loop"
date: 2018-03-07
forum: General Help
---

### Post by panditax on 2018-03-07
Hi

with reference to: [https://ubuntuforums.org/showthread.php?t=2386530](https://ubuntuforums.org/showthread.php?t=2386530).

When I hit "Super+L", display in being locked. I need something like this: when I hit "Super+L" display is being locked, and starting a loop which simulates hitting "Super+L" (lock,lock,lock,lock....n) until I hit ESC for example. Is it possible? Any ideas?

---

### Post by dragonfly41 on 2018-03-07
You could try writing a looping script using **xdotool **available in software centre / Synaptic.

Or you could use a GUI tool to emulate key strokes such as **Actiona** also available in software centre.

---

### Post by panditax on 2018-03-07
xdotool doesn't work :/
I'll check **Actiona** and let know. Thanks for your input.

---

### Post by panditax on 2018-03-26
Couldn't solve this problem with Actiona too. Anything else guys?

---

### Post by dragonfly41 on 2018-03-26
Here is a three action script .. in Actiona utility

Press Meta (i.e. "Super") + L keys
Log actions to console
Loop back to start 5 times


Super+L.ascr script created in Actiona:-
```

<?xml version="1.0" encoding="UTF-8"?>
<scriptfile>
    <settings program="actiona" version="3.9.1" scriptVersion="1.1.0" os="GNU/Linux"/>
    <actions>
        <action name="ActionConsole" version="1.0.0"/>
        <action name="ActionLoop" version="1.0.0"/>
        <action name="ActionKey" version="1.0.0"/>
    </actions>
    <parameters/>
    <resources/>
    <script pauseBefore="0" pauseAfter="0">
        <action name="ActionKey" comment="Super+L">
            <exception id="2" action="1" line=""/>
            <exception id="0" action="0" line=""/>
            <exception id="1" action="0" line=""/>
            <exception id="32" action="0" line=""/>
            <exception id="33" action="0" line=""/>
            <parameter name="shift">
                <subParameter name="value" code="0">false</subParameter>
            </parameter>
            <parameter name="key">
                <subParameter name="key" code="0">L</subParameter>
                <subParameter name="isQtKey" code="0">true</subParameter>
            </parameter>
            <parameter name="ctrl">
                <subParameter name="value" code="0">false</subParameter>
            </parameter>
            <parameter name="amount">
                <subParameter name="value" code="0">1</subParameter>
            </parameter>
            <parameter name="meta">
                <subParameter name="value" code="0">true</subParameter>
            </parameter>
            <parameter name="action">
                <subParameter name="value" code="0">pressRelease</subParameter>
            </parameter>
            <parameter name="alt">
                <subParameter name="value" code="0">false</subParameter>
            </parameter>
            <parameter name="pause">
                <subParameter name="value" code="0">10</subParameter>
            </parameter>
            <parameter name="type">
                <subParameter name="value" code="0">Win32</subParameter>
            </parameter>
        </action>
        <action name="ActionConsole" comment="log presses">
            <exception id="2" action="1" line=""/>
            <exception id="0" action="0" line=""/>
            <exception id="1" action="0" line=""/>
            <parameter name="text">
                <subParameter name="value" code="0">press Super+L</subParameter>
            </parameter>
            <parameter name="output">
                <subParameter name="value" code="0">information</subParameter>
            </parameter>
        </action>
        <action name="ActionLoop">
            <exception id="2" action="1" line=""/>
            <exception id="0" action="0" line=""/>
            <exception id="1" action="0" line=""/>
            <parameter name="count">
                <subParameter name="value" code="0">4</subParameter>
            </parameter>
            <parameter name="line">
                <subParameter name="value" code="0">1</subParameter>
            </parameter>
        </action>
    </script>
</scriptfile>


```


You can run any script from command line by command .. **actexec <scriptname>.ascr**

And run ... **actexec --help** ... to see options available.

QED

---

### Post by HermanAB on 2018-03-26
Autokey is my favourite

---

### Post by panditax on 2018-03-29
It doesn't work :/ My account is not being locked when I execute your script. . I can only see a window with comments "press Super+L". Ubuntu 17.10.

---

### Post by dragonfly41 on 2018-03-29
The script was intended to be a kick start so that you can experiment.

Does your account lock if you manually press Super+L?

Did you try varying the pause period between presses?
In the Key action the default (see Advanced tab) 10 ms but you might try making that a longer period perhaps once a second.
Or you could add a Pause action in the loop (same effect as above).

And you could try increasing the number of loops.

...

Now looking at the root reason for this experiment ...

[https://ubuntuforums.org/showthread.php?t=2386530](https://ubuntuforums.org/showthread.php?t=2386530)

perhaps you can control multiple monitors from the Actiona script?

---

### Post by panditax on 2018-03-29
I'm not the guy like "Do all for me, I just copy paste". I made a script in Actiona on my own previously, but it didn't work at all, so I drop it. Now I have used yours and it doesn't work as well. I tried to modify everything, it looks like Actiona can't press "Meta" button.

> Does your account lock if you manually press Super+L?
Really? Yes, it does :D

@HermanAB
Thanks man, I'll give it a try.

---

### Post by again? on 2018-03-29
You may want to explain why you need this as there may be better solutions.

---

### Post by dragonfly41 on 2018-03-29
> [COLOR=#000000]I made a script in Actiona on my own previously, but it didn't work at all, so I drop it.[/COLOR]

Why didn't you explain this at outset to avoid wasted time?

---

### Post by panditax on 2018-03-29
@up

I did.... More less :P Hope you haven't wasted a whole day for that :)
> **panditax said:**
> Couldn't solve this problem with Actiona too. Anything else guys?

@guber2
Check the link in my first post please.

---

