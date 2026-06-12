---
title: "gnome-shell CPU usage spikes"
date: 2022-01-31
forum: General Help
---

### Post by mauro87 on 2022-01-31
Hello,

For the last few weeks, I've been noticing that my system will randomly hang for 5 minutes before resuming. After doing some digging, I narrowed it down to the gnome-shell process which seems to spike to 100% at random before going back down to below 1%. I captured some logs and it appears that the following happens right before the spike:

Jan 31 21:28:11 prestige gnome-shell[1386]: Some code accessed the property 'CredentialManager' on the module 'credentialManager'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Jan 31 21:28:11 prestige gnome-shell[1386]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
Jan 31 21:28:11 prestige gnome-shell[1386]: Will monitor session c1
Jan 31 21:28:11 prestige gnome-shell[1386]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Jan 31 21:28:11 prestige gnome-shell[1386]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 24]: reference to undefined property "MetaWindowX11"
Jan 31 21:28:11 prestige gnome-shell[1386]: Registering session with GDM

I've tried disabling all extensions but the issue persists. Does anyone know what the issue might be or can possibly point me in the right direction?

---

