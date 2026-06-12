---
title: "Ubuntu 18.04.5 LTS system / software upate -  Visual Code Editor Crash"
date: 2021-08-16
forum: General Help
---

### Post by kami123 on 2021-08-16
Hi (from a newbie),

following a software / system update, I am unable to open Visual Code Editor anymore (Blank screen leading to the popup window below asking me to wait or reopen the application to no avail)

I am seeing a popup window saying : "The window has crashed (reason : 'crashed', code .'132')"

My system : 

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic
```

I tried uninstalling and installing again Visual Code Editor, entered a few Terminal commands I found online to solve the issue but it did not change anything.

Apparently, the application files are located here : /usr/bin/code  but I don't know as an Ubuntu newbie where to look for errors log files leading me to a solution.  

Every other application works perfectly fine (including Atom), no problem with Ubuntu at all.

Thanks a lot for your help, time and patience.

Regards,

Kami

(additional infos : when I enter kbarut@klaptop:/usr/bin$ code --verbose, this is what I get )

```
main 2021-08-16T17:23:42.354Z] Starting VS Code
[main 2021-08-16T17:23:42.357Z] from: /usr/share/code/resources/app
[main 2021-08-16T17:23:42.357Z] args: {
  _: [],
  diff: false,
  add: false,
  goto: false,
  'new-window': false,
  'reuse-window': false,
  wait: false,
  help: false,
  'list-extensions': false,
  'show-versions': false,
  version: false,
  verbose: true,
  status: false,
  'prof-startup': false,
  'no-cached-data': false,
  'prof-v8-extensions': false,
  'disable-extensions': false,
  'disable-gpu': false,
  telemetry: false,
  debugRenderer: false,
  logExtensionHostCommunication: false,
  'skip-release-notes': false,
  'skip-welcome': false,
  'disable-telemetry': false,
  'disable-updates': false,
  'disable-keytar': false,
  'disable-workspace-trust': false,
  'disable-crash-reporter': false,
  'crash-reporter-id': 'e78d407c-2a66-4ead-9ae9-a10c09975c58',
  'skip-add-to-recently-opened': false,
  'unity-launch': false,
  'open-url': false,
  'file-write': false,
  'file-chmod': false,
  'driver-verbose': false,
  force: false,
  'do-not-sync': false,
  trace: false,
  'force-user-env': false,
  'force-disable-user-env': false,
  'open-devtools': false,
  __sandbox: false,
  'no-proxy-server': false,
  'no-sandbox': false,
  nolazy: false,
  'force-renderer-accessibility': false,
  'ignore-certificate-errors': false,
  'allow-insecure-localhost': false,
  logsPath: '/home/kbarut/.config/Code/logs/20210816T192342'
}
[main 2021-08-16T17:23:42.359Z] Resolving machine identifier...
[main 2021-08-16T17:23:42.359Z] Resolved machine identifier: b7d73843bc360d83bc33bae9dcb3c500f349d44636e85e6c7d9b9bf5cd1e18b2
[main 2021-08-16T17:23:42.360Z] Main->SharedProcess#connect
[main 2021-08-16T17:23:42.468Z] StorageMainService: creating global storage
[main 2021-08-16T17:23:42.468Z] lifecycle (main): phase changed (value: 2)
[main 2021-08-16T17:23:42.469Z] windowsManager#open
[main 2021-08-16T17:23:42.469Z] windowsManager#open pathsToOpen [
  {
    backupPath: '/home/kbarut/.config/Code/Backups/1629020038834',
    remoteAuthority: undefined
  }
]
[main 2021-08-16T17:23:42.470Z] IPC Object URL: Registered new channel vscode:985c8b3a-6b04-426e-88f4-339cfef5cce3.
[main 2021-08-16T17:23:42.471Z] window#validateWindowState: validating window state on 1 display(s) { mode: 1, x: 171, y: 57, width: 1024, height: 711 }
[main 2021-08-16T17:23:42.471Z] window#validateWindowState: 1 monitor working area { x: 67, y: 27, width: 1299, height: 741 }
[main 2021-08-16T17:23:42.471Z] window#ctor: using window state { mode: 1, x: 171, y: 57, width: 1024, height: 711 }
[main 2021-08-16T17:23:42.471Z] window: using vscode-file:// protocol and V8 cache options: bypassHeatCheck
[main 2021-08-16T17:23:42.584Z] windowsManager#open used window count 1 (workspacesToOpen: 0, foldersToOpen: 0, emptyToRestore: 1, emptyToOpen: 0)
[main 2021-08-16T17:23:42.585Z] lifecycle (main): phase changed (value: 3)
[main 2021-08-16T17:23:42.586Z] update#setState idle
[main 2021-08-16T17:23:42.586Z] resolveShellEnv(): skipped (VSCODE_CLI is set)
[main 2021-08-16T17:23:59.109Z] CodeWindow: detected unresponsive
Gtk-Message: 19:23:59.149: GtkDialog mapped without a transient parent. This is discouraged.
[main 2021-08-16T17:24:02.003Z] IPC Object URL: Removed channel vscode:985c8b3a-6b04-426e-88f4-339cfef5cce3.
[main 2021-08-16T17:24:02.004Z] Lifecycle#window.on('closed') - window ID 1
[main 2021-08-16T17:24:02.005Z] Lifecycle#onWillShutdown.fire()
[main 2021-08-16T17:24:02.008Z] Lifecycle#app.on(window-all-closed)
[main 2021-08-16T17:24:02.008Z] Lifecycle#app.on(before-quit)
[main 2021-08-16T17:24:02.009Z] Lifecycle#onBeforeShutdown.fire()
[main 2021-08-16T17:24:02.009Z] [WindowsStateHandler] onBeforeShutdown {
  lastActiveWindow: {
    workspaceIdentifier: undefined,
    folder: undefined,
    backupPath: '/home/kbarut/.config/Code/Backups/1629020038834',
    remoteAuthority: undefined,
    uiState: [Object: null prototype] {
      mode: 1,
      x: 171,
      y: 57,
      width: 1024,
      height: 711
    }
  },
  lastPluginDevelopmentHostWindow: undefined,
  openedWindows: []
}
[main 2021-08-16T17:24:02.009Z] Lifecycle#app.on(will-quit)
[main 2021-08-16T17:24:02.015Z] StorageMainService: closed global storage
kbarut@klaptop:/usr/bin$ 
```

---

### Post by kami123 on 2021-08-16
(additional infos) :

in my "code" subdirectory in the snap folder below, I have the three following empty folders but I don't know if I  should delete them or not.

kbarut@klaptop:~/snap/code$ dir

71  common  current

Thanks,

Kami

---

### Post by dragonfly41 on 2021-08-16
I do have VSCode (and Atom) installed on Ubuntu 20.04 so we can compare notes.

I found one suggestion for Ubuntu 18.04 (which incidentally is past its support date) here:

[https://stackoverflow.com/questions/48564668/visual-studio-code-window-has-crashed/50907169](https://stackoverflow.com/questions/48564668/visual-studio-code-window-has-crashed/50907169)


$ cd ~/.config/Code
$ rm -rf Cache/
$ rm -rf CacheData/
$ rm -rf CacheExtensions/


Also inspect logs.

[FONT=monospace][COLOR=#5454FF]**~/.config/Code/logs**[/COLOR]
[/FONT]

---

### Post by deadflowr on 2021-08-16
> I found one suggestion for Ubuntu 18.04 (which incidentally is past its support date) here:

18.04 is supported for another two years-ish. (Like a year and 9 months or so.)

---

### Post by dragonfly41 on 2021-08-16
Sorry .. half asleep.

---

### Post by kami123 on 2021-08-17
Hi dragonfly41 & deadflowr,

I tried what you suggested but it did not change anything.

See the two screenshots here below: 

[https://ibb.co/d7kFQH2](https://ibb.co/d7kFQH2)

[https://ibb.co/9cC5xk3](https://ibb.co/9cC5xk3)

(Btw, I must have tried at least 20 times in the last 6 months to update my system to Ubuntu 20.04 Focal Fossa, every application on my system updates with no problems whatsoever except Ubuntu itself. Definitely not working, it is a serious bug and a waste of efforts.)

Any ideas which logs/ how to check the logs on the first screenshot ?

Thanks.

K.

---

### Post by dragonfly41 on 2021-08-17
You can read the logfile

~/.config/Code/logs/20210816T194631/cli.log

It seems that there have been about 7 log sessions yesterday since 2021/08/16

......

However, rather than trying to debug your installation it might be easier to reinstall.

But first I would disable (not delete) your entire ~/.config/Code/ directory by just remaining it to ~/.config/bak-Code/ directory or some other name.


Also note extensions here ..

~/.vscode

which you might wish to also disable temporarily.

Keep the disabled folders for reference after reinstall and when VSCode is working again you can remove these disabled folders.

[https://code.visualstudio.com/docs/editor/extension-marketplace#_where-are-extensions-installed](https://code.visualstudio.com/docs/editor/extension-marketplace#_where-are-extensions-installed)

Explore reinstall tips such as this ...

[https://www.codegrepper.com/code-examples/shell/how+to+reinstall+vscode+from+scratch+in+ubuntu](https://www.codegrepper.com/code-examples/shell/how+to+reinstall+vscode+from+scratch+in+ubuntu)

and here

[https://superuser.com/questions/1113022/how-do-i-remove-vs-code-settings-from-ubuntu](https://superuser.com/questions/1113022/how-do-i-remove-vs-code-settings-from-ubuntu)

---

