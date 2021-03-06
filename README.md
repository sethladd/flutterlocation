# Flutter Location Plugin

This plugin handle getting location on Android and iOS. It also provides callbacks when location is changed.

## Getting Started

In order to use this plugin in Android, you have to add this permission in AndroidManifest.xml :
```xml
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

And to use it in iOS, you have to add this permission in Info.plist :
```xml
NSLocationWhenInUseUsageDescription
NSLocationAlwaysUsageDescription
```

Then you just have to import the package with
```dart
import 'package:location/location.dart';
```

Look into the example for utilisation, but a basic implementation can be done like this for one time call :
```dart
Map<String,double> _currentLocation;

Location _location = new Location();
// Platform messages may fail, so we use a try/catch PlatformException.
try {
  _currentLocation = await _location.getLocation;
} on PlatformException {
  _currentLocation = null;
}
```

You can also get continuous callbacks when your position is changing :
```dart
StreamSubscription<Map<String,double>> _locationSubscription;
Location _location = new Location();

_locationSubscription =
    _location.onLocationChanged.listen((Map<String,double> result) {
      _currentLocation = result;
    });
```

You can then use the position :
```dart
print(_currentLocation["latitude"]);
print(_currentLocation["longitude"]);
```

## Feedback
Please feel free to give me any feedback helping support this plugin !
