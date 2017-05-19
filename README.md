## Android Runtime Optimization

Android Lollipop includes a new virtual machine called ART (Android Runtime.) ART uses AOT (ahead-of-time) compilation into native code, which performs better than JIT (just-in-time) compilation into bytecode. You can configure ART to perform this optimization in different ways.
Android Lollipop includes the dex2oat tool for optimizing applications on deployment.

### Compiler Filters

In L, dex2oat takes a variety of --compiler-filter options to control how it compiles. Passing in a compiler filter flag for a particular app specifies how it’s pre-optimized. Here’s a description of each available option:

 * **_everything_** - compiles almost everything, excluding class initializers and some rare methods that are too large to be represented by the compiler’s internal representation.
 * **_speed_** - compiles most methods and maximizes runtime performance, which is the default option.
 * **_balanced_** - attempts to get the best performance return on compilation investment.
 * **_space_** - compiles a limited number of methods, prioritizing storage space.
 * **_interpret-only_** - skips all compilation and relies on the interpreter to run code.
 * **_verify-none_** - special option that skips verification and compilation, should be used only for trusted system code.

### Preference

You can change the default compiler filter with the one you prefer (or want to experiment with).
Just go to [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm) and then type:

	art_magisk
![art_magisk](http://i.imgur.com/1HmveXF.png)

And then it'll present you with a menu that is pretty simple and easy to work with.
![art_magisk menu](http://i.imgur.com/OCME41l.png)

### UNIFIED Installer

With unified installer, the zip now installs whether you use Magisk, SuperSU or, if no other stuff is detected, Init.d.
It installs in this order according to detection:
` > Magisk > Systemless SuperSU > System SuperSU > Init.d`


### Changelog
#### v1.1
* Logging Improved
* Saved compiler filter now survives updates on both Magisk and Non-Magisk (unless something prevents it to)
* Moved dalvik.vm.dex2oat-thread_count back to system.prop
* Add dalvik.vm.dex2oat-threads
* Add dalvik.vm.boot-dex2oat-threads
#### v1
* Unified Installer
* dalvik.vm.dex2oat-thread_count is now only applied Android 6+
#### v0.9.1
* Change dalvik.vm.dexopt-flags value to v=a,o=v
#### v0.9
* Added dalvik.vm.dexopt-flags
* Logging fixes
#### v0.8.5
* Code Optimization
* Moved dalvik.vm.heaptargetutilization to be used on Android 5.0+
#### v0.8.2
* Fix more problems
#### v0.8.1
* Fix logging and setting properties
#### v0.8
* Added dalvik.vm.heaptargetutilization
* Logging to /cache/magisk.log added
#### v0.7.5
* Added dalvik.vm.dex2oat-thread_count which will "supposedly" make app installation faster
#### v0.7
* Added pm.dexopt.bg-dexopt for 7.1+
* Added dalvik.vm.dex2oat-swap for 7.1+ (enabled for low mem devices, disabled if not)
#### v0.6 
* Fixed bootloop issues
#### v0.5 
* Added more properties
* Does not overwrite saved filter every update
* Removed post-fs-data.sh and service.sh
#### v0.4 
* Now has a UI in Terminal Emulator (how to use is in the OP)
* Default compiler filter is speed
* Automatically wipes dalvik-cache after flashing
#### v0.3.1 
* fixed typo in post-fs-data.sh and service.sh
#### v0.3 
* post-fs-data.sh and service.sh now reads from system.prop
#### v0.2 
* post-fs-data.sh and service.sh is additionally used on setting properties
#### v0.1 
* Initial Release


[More info about this topic here](https://source.android.com/devices/tech/dalvik/configure)

[See XDA Thread](https://forum.xda-developers.com/apps/magisk/module-android-runtime-optimization-t3596559)

[Non-Magisk](https://www.androidfilehost.com/?w=files&flid=178198)
