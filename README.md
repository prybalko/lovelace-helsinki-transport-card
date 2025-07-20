# Lovelace card for Helsinki (HSL) transport integration

Custom lovelace card that displays upcoming departures from your defined public transport stops for Helsinki.

**The integration itself can be found here: https://github.com/prybalko/home-assistant-helsinki-transport**

This card works only after you installed and configured the integration.

![](./docs/screenshots/timetable-card.jpg)

> I use [iOS Dark Mode Theme](https://github.com/basnijholt/lovelace-ios-dark-mode-theme) by @basnijholt, installed from [HACS](https://hacs.xyz/)

## 💿 Installation

This Lovelace card can be installed via [HACS](https://hacs.xyz/) or manually.

> ⚠️ Make sure you installed the [BVG integration](https://github.com/prybalko/home-assistant-helsinki-transport) first. This card would not work without it.

### Using HACS

**1.** Open HACS interface from your Home Assistant sidebar

**2.** Add [this repository](https://github.com/prybalko/lovelace-helsinki-transport-card) as a custom repository (Three dots in top right corner -> Custom repositories)

**3.** Select "Lovelace" as a category

**4.** Go to `Settings -> Devices & Services -> Add integration` and search for this card name (just type `Helsinki`)

**5.** Install it. Now you can add it to your dashboard


### Installing the card manually

**1.** Copy the [helsinki-transport-card.js](./dist) card module to the `www` directory of your Home Assistant. The same way you did for the sensor above. If it doesn't exist — create one.

**2.** Go to your Home Assistant dashboard, click "Edit dashboard" at the right top corner and after that in the same top right corner choose "Manage resources".

**3.** Add new resource with URL: `/local/helsinki-transport-card.js` and click create. Go back to your dashboard and refresh the page.

**4.** Now you can add the custom card and integrate it with your sensor. Click "Add card -> Manual" or just go to "Raw configuration editor" and use this config.

```yaml
- type: custom:helsinki-transport-card
  show_stop_name: true # show or hide the name of your stop in card title
  max_entries: 8 # number of upcoming departures to show (max: 10)
  entities:
    - sensor.stop_id_900110001 # use your entity IDs here
    - sensor.stargarder_str # they might be different from mine
  show_cancelled: true # show or hide the cancelled departures. When not defined or true, the cancelled departures will be shown as struk-through.
  show_delay: true # show or hide the delay if reported. When not defined or true, the delay will be shown next to the departure time.
  show_absolute_time: true # show the absolute time till departure.
  show_relative_time: true # show the relative time till departure.
  include_walking_time: true # subtract walking time to the stop from the relative time to the departure.
```


## 🎨 Styling

If you want to change any styles, font size or layout — the easiest way is to use [card_mod](https://github.com/thomasloven/lovelace-card-mod) component. It allows you to change any CSS classes to whatever you want.

## ❤️ Contributions

Contributions are welcome. Feel free to [open a PR](https://github.com/prybalko/lovelace-helsinki-transport-card/pulls) and send it to review. If you are unsure, [open an Issue](https://github.com/prybalko/lovelace-helsinki-transport-card/issues) and ask for advice.

## 🐛 Bug reports and feature requests

Since this is my small hobby project, I cannot guarantee you a 100% support or any help with configuring your dashboards. I hope for your understanding.

## 👮‍♀️ License

- [MIT](./LICENSE.md)
