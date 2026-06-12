---
title: "developer tools not opening after update - only one profile affected"
date: 2023-09-29
forum: General Help
---

### Post by talexandre on 2023-09-29
[COLOR=#1F1F1F][FONT=&amp]After updating chrome under Ubuntu to version 117.0.5938.92, I couldn't anymore open the developer tools. Neither via context menu, via the three dots in the window -> more tools and also not via short key. The options are still all shown, but it's just not happening. Though the devtools appear in the chrome task manager, the window is just now showing (also not on other screens or workspaces in the window list). DevTools should open in a new window as before, because I had them undocked.[/FONT][/COLOR][COLOR=#1F1F1F][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]After opening chrome via console, I could see that whenever I try to open the developer console, the following errors occurs:[/FONT][/COLOR]
> [COLOR=#1F1F1F][FONT=&amp]&#8203;[172507:172507:0927/130330.570974:ERROR:CONSOLE(1)] "Uncaught (in promise) QuotaExceededError: Failed to set a named property on 'Storage': Setting the value of 'experiments' exceeded the quota.", source: devtools://devtools/bundled/devtools-frontend/front_end/core/root/root.js (1)&#8203;[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]Then I tried the developer console in another chrome profile and there it still works.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]What can cause this error and how to fix this? I would like to avoid recreating the whole profile.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&amp]Thanks in advance![/FONT][/COLOR]

---

### Post by TheFu on 2023-10-01
Seems you've figured out the issue is in the profile settings.  It would make sense to compare the working and non-working profiles.  I can't help with that.  I've never used Google-Chrome.  In other browsers, profile settings are often javascript or json files, which can be compared using a tool like **meld**.

It might also be a specific addon that's incompatible with the updated release.  Can you run the browser with all addons turned off, but use the same profile?  Will the DevTools open then?

---

### Post by talexandre on 2023-10-02
Thank you for your reply.

I tried opening chrome without any addons / extensions / plugins. Unfortunately, that didn't help with my problem.

 My main profile preferences are pretty big compared to the other profiles. Anyway I compared them and checked some of the differences. Also I tried just replacing the "faulty" preferences file with a working one which didn't help (opened tabs were gone and devtools are still not working with the same error message). Also I tried just deleting the devtools preferences from the files which was also not working for me.

---

