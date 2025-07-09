## Using the plugin (opens Location Settings in Android and Application Settings in iOS)

This plugin supports both Android and iOS. The `"application_details"` constant opens the settings page of the application on both platforms.

### ✅ iOS Notice (Updated)

The iOS implementation now uses the recommended `UIApplicationOpenSettingsURLString` with `openURL:options:completionHandler:` for full compatibility with iOS 10+. This ensures proper redirection to your app’s settings page using the safest and most future-proof approach.

If your only goal is to open the **application settings on iOS**, and you're not using Cordova or a plugin, you may also use this direct JavaScript fallback:

```javascript
window.open('app-settings:', '_system');

## Adding/Removing the Plugin
It will be saved to the config.xml file

Ionic Framework:

```bash
ionic cordova plugin (add|rm) cordova-open-native-settings
```

Cordova:

```bash
cordova plugin (add|rm) cordova-open-native-settings --save
```

or via npm (It will be saved to the package.json file)

```bash
npm (install|uninstall) cordova-open-native-settings --save
```

## Using the plugin (opens Location Settings in Android and Application Settings in iOS)

```
cordova.plugins.settings.open(setting_constant, success_callback, failure_callback);
```

### Example for iOS and Android - open Wifi settings

```js
if (window.cordova && window.cordova.plugins.settings) {
    console.log('openNativeSettingsTest is active');
    window.cordova.plugins.settings.open("wifi", function() {
            console.log('opened settings');
        },
        function () {
            console.log('failed to open settings');
        }
    );
} else {
    console.log('openNativeSettingsTest is not active!');
}
```

In Android, by default it is opened in the same application as a new activity, the hardware back button will bring the user back to the previous activity (the app). In order to open settings as a new application (two applications will appear in "recent/opened" apps list) the following code can be used:
`window.cordova.plugins.settings.open(["wifi", true], function() {}, function() {}); ....`

## Settings Options (Android)

Setting constant | Description
-----------------|------------
"accessibility" | Show settings for accessibility modules
"account" | Show add account screen for creating a new account
"airplane_mode" | Show settings to allow entering/exiting airplane mode
"apn" | Show settings to allow configuration of APNs
"application_details" | Show screen of details about a particular application
"application_development" | Show settings to allow configuration of application development-related settings
"application" | Show settings to allow configuration of application-related settings
"battery_optimization" | Show screen for controlling which apps can ignore battery optimizations
"biometric" | Show screen for configuring biometric based device security
"bluetooth" | Show settings to allow configuration of Bluetooth
"captioning" | Show settings for video captioning
"cast" | Show settings to allow configuration of cast endpoints
"data_roaming" | Show settings for selection of 2G/3G
"date" | Show settings to allow configuration of date and time
"display" | Show settings to allow configuration of display
"dream" | Show Daydream settings
"home" | Show Home selection settings
"keyboard" | Show settings to configure input methods, in particular allowing the user to enable input methods
"keyboard_subtype" | Show settings to enable/disable input method subtypes
"locale" | Show settings to allow configuration of locale
"location" | Show settings to allow configuration of current location sources
"manage_all_applications" | Show settings to manage all applications
"manage_applications" | Show settings to manage installed applications
"memory_card" | Show settings for memory card storage
"network" | Show settings for selecting the network operator
"nfcsharing" | Show NFC Sharing settings
"nfc_payment" | Show NFC Tap & Pay settings
"nfc_settings" | Show NFC settings
"notification_id" | Settings > Notifications
"print" | Show the top level print settings
"privacy" | Show settings to allow configuration of privacy options
"quick_launch" | Show settings to allow configuration of quick launch shortcuts
"search" | Show settings for global search
"security" | Show settings to allow configuration of security and location privacy
"settings" | Show system settings
"show_regulatory_info" | Show the regulatory information screen for the device
"sound" | Show settings to a llow configuration of sound and volume
"storage" | Show settings for internal storage
"store" | Open the Play Store page of the current application
"sync" | Show settings to allow configuration of sync settings
"usage" | Show settings to control access to usage information
"user_dictionary" | Show settings to manage the user input dictionary
"voice_input" | Show settings to configure input methods, in particular allowing the user to enable input methods
"wifi_ip" | Show settings to allow configuration of a static IP address for Wi-Fi
"wifi" | Show settings to allow configuration of Wi-Fi
"wireless" | Show settings to allow configuration of wireless controls such as Wi-Fi, Bluetooth and Mobile networks


## Settings Options (iOS)

Setting constant | Description
-----------------|------------
"about" | Settings > General > About
"accessibility" | Settings > General > Accessibility
"account" | Settings > _Your name_
"airplane_mode" | Settings > Airplane Mode
"application_details" | Settings
"autolock" | Settings > General > Auto-Lock (before iOS 10)
"battery" | Settings > Battery
"bluetooth" | Settings > General > Bluetooth (before iOS 9)<br>Settings > Bluetooth (after iOS 9)
"browser" | Settings > Safari
"castle" | Settings > iCloud
"cellular_usage" | Settings > General > Cellular Usage
"configuration_list" | Settings > General > Profile
"date" | Settings > General > Date & Time
"display" | Settings > Display & Brightness
"do_not_disturb" | Settings > Do Not Disturb
"facetime" | Settings > Facetime
"keyboard" | Settings > General > Keyboard
"keyboards" | Settings > General > Keyboard > Keyboards
"locale" | Settings > General > Language & Region
"location" | Settings > Location Services (in older versions of iOS)
"locations" | Settings > Privacy > Location Services (in newer versions of iOS)
"tracking" | Settings > Privacy > Tracking (iOS 14+)
"mobile_data" | Settings > Mobile Data (after iOS 10)
"music" | Settings > iTunes
"music_equalizer" | Settings > Music > EQ
"music_volume" | Settings > Music > Volume Limit
"network" | Settings > General > Network
"nike_ipod" | Settings > Nike + iPod
"notes" | Settings > Notes
"notification_id" | Settings > Notifications
"passbook" | Settings > Passbook & Apple Pay
"phone" | Settings > Phone
"photos" | Settings > Photo & Camera
"privacy" | Settings > Privacy
"reset" | Settings > General > Reset
"ringtone" | Settings > Sounds > Ringtone
"search" | Settings > General > Assistant (before iOS 10)<br>Settings > Siri (after iOS 10)
"settings" | Settings > General
"sound" | Settings > Sounds
"software_update" | Settings > General > Software Update
"storage" | Settings > iCloud > Storage & Backup
"store" | Settings > iTunes & App Store
"tethering" | Settings > Personal Hotspot
"touch" | Settings > Touch ID & Passcode
"twitter" | Settings > Twitter
"usage" | Settings > General > Storage & iCloud Usage
"video" | Settings > Video
"vpn" | Settings > General > VPN
"wallpaper" | Settings > Wallpaper
"wifi" | Settings > WIFI


##Notes
*Android plugin based on: https://developer.android.com/reference/android/provider/Settings.html#ACTION_DREAM_SETTINGS
*iOS plugin now uses UIApplicationOpenSettingsURLString and openURL:options:completionHandler: (safe for iOS 10+)
*Full support for opening app settings ("application_details") in line with App Store guidelines
*Legacy iOS schemes like "prefs:" or "App-Prefs:" have been removed for compliance
*The plugin for Android is based on a forked repository and was refactored. The iOS part was built from scratch and later modernized.
*If you're only targeting app settings in iOS, you can use window.open('app-settings:', '_system') directly.

## License
```
The MIT License

Copyright (c) 2016 Guy Rombaut

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
