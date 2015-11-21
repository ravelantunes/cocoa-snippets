This repository is collection of code snippets that I started collecting while working on Objective-C/Swift code, so I
could quick reference it.

After working a few years in various projects, I realized that I was constantly Googling or referencing older projects
for pieces of code to achieve results I've done before, since I just wasn't able to remember how I've solved them
previously.
 
Feel free to contribute with any comments or pull requests.
 
 
# Objective-C Specifics

## Static Properties
 
 ``` Objective-C
 static NSString *myStaticString;
 ```
 
 ## Random Int
 
 Get a random int between 1 and 4:
 
 ``` Objective-C
 arc4random_uniform(4)+1
 ```
 
# UIKit


## UIButton

### Set highlighted state for a button that is selected
 When setting an image for the `UIControlStateHighlighted` state of a UIButton, that image will only be used to
 highlight the state for when the button is not selected. To have a highlight state for a selected button, you need to
 set an image for the state `UIControlStateSelected | UIControlStateHighlighted` (Button control state uses bitmasks).  
 
``` Objective-C
[button setBackgroundImage:[UIImage imageNamed:@"button_image_selected"] forState:UIControlStateSelected | UIControlStateHighlighted];
```
 
## UINavigationBar
 
### Setting custom background


For portrait:

``` Objective-C
[self.navigationBar setBackgroundImage:[UIImage imageNamed:@"navigation-bar-background"] forBarMetrics:UIBarMetricsDefault];
```

For landscape:

``` Objective-C
[self.navigationBar setBackgroundImage:[UIImage imageNamed:@"navigation-bar-background"] forBarMetrics: UIBarMetricsCompact];
```

## UITextField

### Change placeholder font color

``` Objective-C
UITextField *textField = [UITextField alloc] init];
UIColor *color = [UIColor lightTextColor];
textField.attributedPlaceholder = [[NSAttributedString alloc] initWithString:@"PlaceHolder Text" attributes:@{NSForegroundColorAttributeName: color}];
```

Or you can do this to keep the same current text that the placeholder have:

``` Objective-C
self.searchTextField.attributedPlaceholder = [[NSAttributedString alloc] initWithString:self.searchTextField.placeholder attributes:@{NSForegroundColorAttributeName: [UIColor lightTextColor]}];
```

## UITextView

### Handle return to dismiss textView, instead of adding new line

``` Objective-C

- (BOOL)textView:(UITextView *)textView shouldChangeTextInRange:(NSRange)range replacementText:(NSString *)text {
    NSRange resultRange = [text rangeOfCharacterFromSet:[NSCharacterSet newlineCharacterSet] options:NSBackwardsSearch];
    if ([text length] == 1 && resultRange.location != NSNotFound) {
        [textView resignFirstResponder];
        return NO;
    }

    return YES;
}

```


## NSAttributedString

### Defining letters spacing

The letter spacing is determined by the NSKernAttributeName attribute constant. 


``` Objective-C
NSMutableAttributedString *attributedString = [[NSMutableAttributedString alloc] initWithString:@"My String!"];
[attributedString addAttribute:NSKernAttributeName
                         value:@(1.5)
                         range:NSMakeRange(0, 10)];
```



## UIFont

### List all fonts installed
``` Objective-C
NSArray *fontFamilies = [UIFont familyNames];

for (int i = 0; i < [fontFamilies count]; i++)
{
    NSString *fontFamily = [fontFamilies objectAtIndex:i];
    NSArray *fontNames = [UIFont fontNamesForFamilyName:[fontFamilies objectAtIndex:i]];
    NSLog (@"%@: %@", fontFamily, fontNames);
}
```


## Status Bar

### Controlling appearance

The way to control the appearance of the status bar depends on how you have it setup on your info.plist, with the key
`UIViewControllerBasedStatusBarAppearance`.

#### UIViewControllerBasedStatusBarAppearance as TRUE

``` Objective-C
- (UIStatusBarStyle)preferredStatusBarStyle {
    return UIStatusBarStyleLightContent;
}

```

#### UIViewControllerBasedStatusBarAppearance as FALSE

``` Objective-C
[[UIApplication sharedApplication] setStatusBarStyle:UIStatusBarStyleLightContent];
```

It can also be animated:


``` Objective-C
[[UIApplication sharedApplication] setStatusBarHidden:NO withAnimation:UIStatusBarAnimationSlide];
```


``` Objective-C
```

``` Objective-C
```

``` Objective-C
```

``` Objective-C
```