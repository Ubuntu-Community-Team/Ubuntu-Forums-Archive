---
title: "Matlab 2011b install in 12.10"
date: 2012-11-10
forum: General Help
---

### Post by zgly on 2012-11-10
Hi everyone,

I an trying to install Matlab 2011b from a zip file on my 32 bit machine that runs 12.10. I cannot get it to work. I understand from what I have read on the internet that there might be a "symbolic link" issue, but I do not know what it refers to, and even less how to solve the problem. I also get different error message depending on whether or not I use "sudo", which is highly confusing to me.

Below is what I type, and the error messages I get. using sudo. Any help would be greatly appreciated, thanks.

-Dell:~$ sudo Downloads/MatlabR2011b-glnx86-staff/install &
[1] 3835
-Dell:~$ Preparing installation files ...
Installing ...
Exception in thread "main" com.google.inject.ProvisionException: Guice provision errors:

1) Error in custom provider, java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
  at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:60)
  while locating com.mathworks.instutil.DisplayProperties
  at com.mathworks.wizard.ui.components.ComponentsModule.providePaintStrategy(ComponentsModule.java:76)
  while locating com.mathworks.wizard.ui.components.PaintStrategy
    for parameter 4 at com.mathworks.wizard.ui.components.SwingComponentFactoryImpl.<init>(SwingComponentFactoryImpl.java:110)
  while locating com.mathworks.wizard.ui.components.SwingComponentFactoryImpl
  while locating com.mathworks.wizard.ui.components.SwingComponentFactory
    for parameter 1 at com.mathworks.wizard.ui.WizardUIImpl.<init>(WizardUIImpl.java:65)
  while locating com.mathworks.wizard.ui.WizardUIImpl
  while locating com.mathworks.wizard.ui.WizardUI annotated with @com.google.inject.name.Named(value=BaseWizardUI)
  at com.mathworks.wizard.ui.UIModule.provideWizardUI(UIModule.java:50)
  while locating com.mathworks.wizard.ui.WizardUI
    for parameter 0 at com.mathworks.wizard.ExceptionHandlerImpl.<init>(ExceptionHandlerImpl.java:22)
  while locating com.mathworks.wizard.ExceptionHandlerImpl
  while locating com.mathworks.wizard.ExceptionHandler

1 error
    at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:767)
    at com.google.inject.InjectorImpl.getInstance(InjectorImpl.java:793)
    at com.mathworks.wizard.WizardLauncher.startWizard(WizardLauncher.java:160)
    at com.mathworks.wizard.WizardLauncher.start(WizardLauncher.java:75)
    at com.mathworks.wizard.AbstractLauncher.launch(AbstractLauncher.java:27)
    at com.mathworks.wizard.AbstractLauncher.launchStandalone(AbstractLauncher.java:1
    at com.mathworks.installwizard.Launcher.main(Launcher.java:19)
Caused by: java.lang.RuntimeException: java.lang.reflect.InvocationTargetException
    at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:106)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:75
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
    at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
    at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
    at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
    at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
    at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
    at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
    at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
    at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
    at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
    at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
    at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
    at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
    at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
    at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
    at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
    at com.google.inject.Scopes$1$1.get(Scopes.java:54)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:75
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
    at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
    at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
    at com.google.inject.spi.ProviderLookup$1.get(ProviderLookup.java:89)
    at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:95)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
    at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
    at com.google.inject.Scopes$1$1.get(Scopes.java:54)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.SingleParameterInjector.inject(SingleParameterInjector.java:42)
    at com.google.inject.SingleParameterInjector.getAll(SingleParameterInjector.java:66)
    at com.google.inject.ConstructorInjector.construct(ConstructorInjector.java:84)
    at com.google.inject.ConstructorBindingImpl$Factory.get(ConstructorBindingImpl.java:111)
    at com.google.inject.FactoryProxy.get(FactoryProxy.java:56)
    at com.google.inject.ProviderToInternalFactoryAdapter$1.call(ProviderToInternalFactoryAdapter.java:45)
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:811)
    at com.google.inject.ProviderToInternalFactoryAdapter.get(ProviderToInternalFactoryAdapter.java:42)
    at com.google.inject.Scopes$1$1.get(Scopes.java:54)
    at com.google.inject.InternalFactoryToProviderAdapter.get(InternalFactoryToProviderAdapter.java:4
    at com.google.inject.InjectorImpl$4$1.call(InjectorImpl.java:75
    at com.google.inject.InjectorImpl.callInContext(InjectorImpl.java:804)
    at com.google.inject.InjectorImpl$4.get(InjectorImpl.java:754)
    ... 6 more
Caused by: java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at com.google.inject.internal.ProviderMethod.get(ProviderMethod.java:101)
    ... 54 more
Caused by: com.mathworks.instutil.JNIException: java.lang.UnsatisfiedLinkError: /home/melanie/Downloads/MatlabR2011b-glnx86-staff/bin/glnx86/libinstutil.so: /home/melanie/Downloads/MatlabR2011b-glnx86-staff/bin/glnx86/libstdc++.so.6: file too short
    at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:39)
    at com.mathworks.instutil.NativeUtility.<init>(NativeUtility.java:24)
    at com.mathworks.instutil.DisplayPropertiesImpl.<init>(DisplayPropertiesImpl.java:10)
    at com.mathworks.wizard.WizardModule.provideDisplayProperties(WizardModule.java:67)
    ... 59 more
Caused by: java.lang.UnsatisfiedLinkError: /home/melanie/Downloads/MatlabR2011b-glnx86-staff/bin/glnx86/libinstutil.so: /home/melanie/Downloads/MatlabR2011b-glnx86-staff/bin/glnx86/libstdc++.so.6: file too short
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at com.mathworks.instutil.NativeUtility.loadNativeLibrary(NativeUtility.java:37)
    ... 62 more
Finished

---

### Post by zgly on 2012-11-17
Could anybody help me with this please? Even just a vague suggestion on how to proceed?

---

