---
title: "xfce4-mailwatch failing in gmail"
date: 2022-06-09
forum: General Help
---

### Post by ajgreeny on 2022-06-09
I have been using the xfce4-mailwatch applet in my Xubuntu 20.04 and now 22.04 panels for a long time but it has suddenly stopped working for both pop3 and imap mail accounts, simply telling me in the log file for both systems 
```
Received HTTP Response code 401. The most likely reason for this is that your GMail username or password is incorrect.
```
That is definitely not the case and I wonder if this is related to the need for 2 Factor Authorisation that gmail has started to require and if that can be set in the applet in any way.
If so, does anyone know why has it only begun to fail in the last few days when the 2FA has now been needed for longer than that.

I know some users will suggest that it is not a very secure applet, but I am aware of that and just wonder what might have changed recently.

---

### Post by #&amp;thj^% on 2022-06-09
I'm also talking to them now, here is the first brush off:
> 

To help keep your account secure, from May 30, 2022, &#8203;&#8203;Google no longer supports the use of third-party apps or devices which ask you to sign in to your Google Account using only your username and password.

Important: This deadline does not apply to Google Workspace or Google Cloud Identity customers. The enforcement date for these customers will be announced on the Workspace blog at a later date.

For more information, continue to read.

and when I try:
> Some apps and devices use less secure sign-in technology, which makes your account vulnerable. You can turn off access for these apps, which we recommend, or turn it on if you want to use them despite the risks. Google will automatically turn this setting OFF if it’s not being used.
**This setting is no longer available. Learn more**

---

### Post by ajgreeny on 2022-06-09
Hi 1fallen.

Yes I had already found that after asking the above question and was a bit dismayed as I found it to be extremely useful.
However, I now wonder if there is any way around it; if not the panel applet is useless to me now.

Thank you GMail, for making life a bit more difficult.

I have looked at **birdtray** as an alternative but I can't figure out the configuration of it when started and it almost appears that you have to have thunderbird running permanently for birdtray to work., not the way I use thunderbird or want to use it.

I also wonder if it means that we will in future be unable to use Thunderbird unless we set up 2 Factor Authorisation using a mobile phone or something similar.

---

### Post by #&amp;thj^% on 2022-06-09
> **ajgreeny said:**
> Hi 1fallen.


However, I now wonder if there is any way around it; if not the panel applet is useless to me now.

Thank you GMail, for making life a bit more difficult.

I also wonder if it means that we will in future be unable to use Thunderbird unless we set up 2 Factor Authorisation using a mobile phone or something similar.

Yep, First have to set-up 2factor sign in then add your app via: Sign in with App Passwords

Tip: App Passwords aren&#8217;t recommended and are unnecessary in most cases. To help keep your account secure, use "Sign in with Google" to connect apps to your Google Account. 

**An App Password is a 16-digit passcode that gives a less secure app or device permission to access your Google Account. App Passwords can only be used with accounts that have 2-Step Verification turned on. **
That should get you going again. ***Important after you generate your passcode add it to "mailwatch" which is also exactly the Name i gave it in the drop down box for the app.

> **ajgreeny said:**
> 

Thank you GMail, for making life a bit more difficult.



Your nicer than I was,>>> I'm sure they have a hit out on me. :lolflag:

OK I'm going to make this a little easier to follow not for ajgreeny necessarily but other readers as well.

    Go to your Google Account.
    Select Security.
    Under "Signing in to Google," select App Passwords. You may need to sign in. If you don&#8217;t have this option, it might be because:
        2-Step Verification is not set up for your account.
        2-Step Verification is only set up for security keys.
        Your account is through work, school, or other organization.
        You turned on Advanced Protection.
    At the bottom, choose Select app and choose the app you using and then Select device and choose the device you&#8217;re using and then Generate.
    Follow the instructions to enter the App Password. The App Password is the 16-character code in the yellow bar on your device.
    Tap Done.

Tip: Most of the time, you&#8217;ll only have to enter an App Password once per app or device, so don&#8217;t worry about memorizing it.  (Famous last Words LOL)

---

### Post by ajgreeny on 2022-06-10
I did not use 2FA for very much at all because we live in an area with dreadful mobile signal and it was often impossible to get the 6 figure One Time Authorisation code needed to login to websites.
Having changed mobile network things are now much better but I don't want to have to go through that palaver of a text message OTA each time I want to check emails. 
I think you are suggesting that will not be necessary once a device has been used the first time; is that what you meant?

---

### Post by #&amp;thj^% on 2022-06-10
> **ajgreeny said:**
> 
I think you are suggesting that will not be necessary once a device has been used the first time; is that what you meant?
Yes Sir, once the passcode is entered into mailwatch, Done!
EDIT: The support guy I was talking with, suggested if your 2FA was through your phone you would receive a text verification from time to time, Ive yet to see that, after setting it up with the new work around.
And I'm not sure how that will affect you being across the pond. :)

---

