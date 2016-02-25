HockeyApp gem
=============

This gem enables you to easily access the JSON Rest API of http://www.hockeyapp.net.

More info available on this API here : http://support.hockeyapp.net/kb/api


HOW-TO
======

1° Configure your connection :

```ruby
HockeyApp::Config.configure do |config|
  config.token = "ABCDEF"
end
```

2° Make a client

```ruby
client = HockeyApp.build_client
```

3° Use the client

```ruby
apps = client.get_apps
versions = apps.first.versions
crashes = apps.first.crashes
....
```

4° creating a blank app

new_app(title, bundle_id, options = {})

Parameters:

    title - required, the app's name

    bundle_identifier - required, the bundle identifier on iOS or Mac OS X, the package name on Android, or the namespace on Windows Phone

    platform - optional, the app's platform:
        iOS [default]
        Android
        Mac OS
        Windows Phone
        Custom

    release_type - optional, set the release type of the app:
        2 for alpha
        0 for beta [default]
        1 for store
        3 for enterprise

    custom_release_type - optional, set to the custom release type string

    icon - optional, icon file with content type image/png, image/jpeg, or image image/gif

    private - optional, set to true to enable the private download page (default is true)

    owner_id - optional, set to the ID of your organization

    example - options = {
                          :platform => "iOS", 
                          :release_type => 1, 
                          :custom_release_type => "alpha", 
                          :icon => "/path/to/icon", 
                          :private => true, 
                          :owner_id => "your-Owner/Organization-id"
                        }