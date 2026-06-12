---
title: "Getting a headset button to work with Mumble"
date: 2015-10-27
forum: General Help
---

### Post by EvanEjk on 2015-10-27
I'm trying to get a wireless headset button to work on Mumble. The headset is an "HS-1200 DIGITAL WIRELESS" from "CREATIVE". The volume buttons work great but there is another button on the headset that I would like to use for Mumble.

The box said the button is for windows messenger or something for answering calls and I heard it works for Skype too.

For some reason when I went to set it as a hotkey in Mumble it closed the window. I went to find out what key input the button actually sends with some code like this
```
    GLFWKeyCallback keyCallback = new GLFWKeyCallback(){ 
      @Override 
      public void invoke(long window,int key,int scancode,int action,int mods){
        System.out.printf("%d %d %d %d%n",key,scancode,action,mods);
      }
    };
```

The results showed this. I wrote in what the numbers mean
```
342 64 1 0      GLFW_KEY_LEFT_ALT               PRESS
342 64 0 4      GLFW_KEY_LEFT_ALT       +ALT    RELEASE
67 54 1 4       GLFW_KEY_C              +ALT    PRESS
67 54 0 4       GLFW_KEY_C              +ALT    RELEASE
284 127 1 0     GLFW_KEY_PAUSE                  PRESS
284 127 0 0     GLFW_KEY_PAUSE                  RELEASE
```

Basically the alt+c was triggering the cancel button in Mumble. So I went into the Mumble.conf and set the shortcut to alt+c by hand. It almost worked but it didn't because the computer can't tell the button is being held down. When the button on the headset is pressed it sends the data and when it is released it sends nothing. So I don't think there is any way to tell how long the button on the headset is being held down. What I had in mind was to use the button to toggle the microphone instead. So when I press the button it would turn the mic on until I press the button a next time.

Is there a way I can have some code listen for the alt+c press. And every next press it would either turn the mic on or off based on the last press? And also if it could speak back to me "microphone off" when it turns the mic off that would be nice too so I know if the mic is on or not without having to see the screen. If I got up to this point I don't think it was be very hard to add
```
spd-say -r -50 -p -100 -i -50 -t male2 "Microphone off."
```
And a "microphone on" message would be good too.

---

### Post by EvanEjk on 2015-10-28
Turns out I lucked out and Mumble pretty much supports this toggle feature all ready. In Mumble under advanced configuration I found what I was looking for. Under messages the message named "Other self-mute/deafened" has settings to turn on voice to speech for "muted" and "unmuted". I made a shortcut under "Shortcuts" with the "Mute Self" function and "Toggle" for data. To set the shortcut to alt-c I had to edit this file from  the home directory ".config/Mumble/Mumble.conf" under "[shortcuts]". After changing the "Transmit" setting to "Continuous" it worked as I desired.

---

