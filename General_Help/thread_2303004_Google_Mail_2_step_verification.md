---
title: "Google Mail 2 step verification"
date: 2015-11-15
forum: General Help
---

### Post by Robbyx on 2015-11-15
I could post this in a thunderbird/ firefox/ google  conference but I am hoping I will get better help here as I assume many people use  the 2 part verification system.

I decided to switch on Google's 2 part verification for access to  my google account. That was yesterday. Today I could not download my mail from the google account using pop3. Google would not accept the password. If I went in via Firefox online then I could access the online account and did not need an app password. .

Google's error message indicated that I needed a special app password. I generetated it and was able to go in via pop3. Does this mean that I should always use that app password when accessing Google via thunderbird and I can not revert to the password I set up for access to my google account when using thunderbird. I have tried to use my original password but it just causes me to have to regenerate the app password and it does not give me access via Thunderbird.

---

### Post by deadflowr on 2015-11-15
> [COLOR=#000000]Does this mean that I should always use that app password when accessing Google via thunderbird and I can not revert to the password I set up for access to my google account when using thunderbird.[/COLOR]

Yes, as long as you have 2-step enabled for your account, you'll need to use an app password for thunderbird.

You might need to go to your google settings security page's app password section to revoke the current app password, in order to use a new one.

---

### Post by Robbyx on 2015-11-15
Thank you. Google's comments are ambiguous:

[I][B]Sign in using App Passwords
[/B]
 If you use 2-Step-Verification and are seeing a &#8220;password incorrect&#8221; error when trying to access your Google Account, an App password may solve the problem. Most of the time, you&#8217;ll only have to enter an App password once per app or device, so don&#8217;t worry about memorizing it.

*Why you may need an App password*

When you sign up for 2-Step Verification, we normally send you verification codes. However, these codes do not work with some apps and devices, like Gmail on your iPhone or iPad, Thunderbird, and Outlook. Instead, you&#8217;ll need to authorize the app or device the first time you use it to sign in to your Google Account by generating and entering an App password.

[https://support.google.com/accounts/answer/185833](https://support.google.com/accounts/answer/185833)
[/I]

On the plain reading of their explanation I took it that I orly use the app password once and here is something from the same location that seems to confirm it. 

[I]**Forgot your App password**

Every App password is only used once. But don't worry, you can always generate a new App password whenever you need one, even for a device or application you've authorized before.[/I]

 Do you know how it works when a third party  tries to login to my google account with my user name and app password? this is why I am concerned:

I fear that the app password is a master password useable from any device irrespective of the 2 step setup, again this is because of the ambiguity of Google's explanation.

---

### Post by bapoumba on 2015-11-15
You will need one app password per app.

For ex, using Thunderbird on 2 different computers, you need 2 different app passwords. Once used in one app, it cannot be used again in a different app, so someone trying to log into your account with your app password would need to do it from the Thunderbird instance you assigned it to. Meaning they would be on your computer, that would be much more worrisome that just accessing your google account :)
In other words, no other app, including ones you have on your own machine or phone, can access your account with that password. I have a whole bunch of them, as I routinely use 3 machines and VMs.

You do not need to store the passwords, you can always revoke/create new ones from your google web interface, and add them to TB or other apps. Otherwise, as long as you do not revoke the app password, it will be valid for the one app you created it.

The only thing I worry about is keeping a set of [valid backup codes]("https://support.google.com/accounts/answer/1187538?hl=en") to log in with the google authenticator from web browsers, in case I loose access to my phone (not what you describe here, I know).

---

### Post by deadflowr on 2015-11-15
Perhaps I'm lost on what you find ambiguous about it.

The app password is a one time/ one device / one application password.
If a 3rd party got a hold of your app password, they couldn't do anything with it if you have already used it.
It's tied forever to the app you used it for, and only that app.

The only way to generate a new app password is through your main 2-step accessed account page, so a 3rd party would need to get that in order to generate a new app password.

---

### Post by Robbyx on 2015-11-15
Thank you both. I now not worried and will continue to use the thunderbird app password from within TB, knowing that if someone discovered the app password and tried to use it from their computer logged into my wifi they would not be able to access TB with that particular app password.

---

### Post by bapoumba on 2015-11-15
Well, I'm not sure I see the point of someone sneaking into your network, it would be the same from any access point. 2-steps auth from Google is precisely to increase security. You need 2 auth to log in the web interface, your google password and a code (via sms or google authenticator). The web interface is where you generate app passwords for specific apps, that you can revoke anytime. 

Protect your wifi :)

---

