---
layout: post
title: iOS提示框WHToast
date:   2018-11-19
categories: [iOS]
tags: [tool]
---

# iOS提示框WHToast

[WHToast](https://github.com/remember17/WHToast)是一个轻量级的提示控件，没有任何依赖。

![](../assets/whtoast/whtoast-1.gif)

# 使用方法

### 1. 可以直接去github下载文件拖进工程，也可以使用pod。

```objective-c
pod 'WHToast'
```

### 2. 导入WHToast.h头文件

```objective-c
#import <WHToast.h>
```

### 3. 说明

每种显示类型都有两个方法，第一个方法默认显示在屏幕中间，第二个方法带有originY参数的是可以自定义显示位置，也就是自定义frame.origin.y。（注意：如果传入的originY<=0，也是显示在屏幕中间）。

### 4. 显示文字提示。

```objective-c
// 显示在页面中间，duration代表多久之后消失
[WHToast showMessage:@"测试一下" duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];

// 自定义frame.origin.y
[WHToast showMessage:@"测试一下" originY:200 duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];
```

### 5. 显示带有成功图标的提示。

```objective-c
// 显示在页面中间，duration代表多久之后消失
[WHToast showSuccessWithMessage:@"测试一下" duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];

// 自定义frame.origin.y
[WHToast showSuccessWithMessage:@"测试一下" originY:100 duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];
```

### 6. 带有错误图标的提示。

```objective-c
// 显示在页面中间，duration代表多久之后消失
[WHToast showErrorWithMessage:@"测试一下" duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];

// 自定义frame.origin.y
[WHToast showErrorWithMessage:@"测试一下" originY:200 duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];
```

### 7. 传入一个图片，自定义图标提示。

```objective-c
// 显示自定义图片，如果message传入nil，则只显示图片，duration代表多久之后消失
[WHToast showImage:[UIImage imageNamed:@"123"] message:nil duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];

// 自定义frame.origin.y，显示自定义图片
[WHToast showImage:[UIImage imageNamed:@"123"] message:@"测试一下" originY:200 duration:2 finishHandler:^{
  NSLog(@"省略n行代码");
}];
```

### 8. 下面贴出来[WHToast](https://github.com/remember17/WHToast)的所有方法。

```objective-c

/** 仅文字，展示在屏幕中间 */
+ (void)showMessage:(NSString *)message duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 仅文字，自定义frame.origin.y 如果（originY <= 0）会展示在屏幕中间 */
+ (void)showMessage:(NSString *)message originY:(CGFloat)originY duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 成功图标和文字，展示在屏幕中间 */
+ (void)showSuccessWithMessage:(NSString *)message duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 成功图标和文字，自定义frame.origin.y 如果（originY <= 0）会展示在屏幕中间 */
+ (void)showSuccessWithMessage:(NSString *)message originY:(CGFloat)originY duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 失败图标和文字，展示在屏幕中间 */
+ (void)showErrorWithMessage:(NSString *)message duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 失败图标和文字，自定义frame.origin.y 如果（originY <= 0）会展示在屏幕中间 */
+ (void)showErrorWithMessage:(NSString *)message originY:(CGFloat)originY duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 自定义图片和文字，展示在屏幕中间。 如果message传入nil，则只显示图片 */
+ (void)showImage:(UIImage *)image message:(NSString *)message duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 自定义图片和文字，自定义frame.origin.y 如果（originY <= 0）会展示在屏幕中间。如果message传入nil，则只显示图片 */
+ (void)showImage:(UIImage *)image message:(NSString *)message originY:(CGFloat)originY duration:(NSTimeInterval)duration finishHandler:(dispatch_block_t)handler;

/** 主动消失 */
+ (void)hide;


/******************************************************/
/******************  设置全局样式  **********************/
/******************************************************/

/** 是否有背景遮罩，默认有 */
+ (void)setShowMask:(BOOL)showMask;

/** 遮罩颜色，默认透明 */
+ (void)setMaskColor:(UIColor *)maskColor;

/** 遮罩是否遮住导航栏，默认遮住 */
+ (void)setMaskCoverNav:(BOOL)maskCoverNav;

/** 边距，默认12 */
+ (void)setPadding:(CGFloat)padding;

/** 提示图片尺寸，默认（20,20）*/
+ (void)setTipImageSize:(CGSize)tipImageSize;

/** toast圆角，默认7 */
+ (void)setCornerRadius:(CGFloat)cornerRadius;

/** 提示图片圆角，默认0 */
+ (void)setImageCornerRadius:(CGFloat)cornerRadius;

/** 背景颜色，默认[UIColor colorWithWhite:0 alpha:0.8] */
+ (void)setBackColor:(UIColor *)backColor;

/** 成功/失败 图标颜色，默认白色 */
+ (void)setIconColor:(UIColor *)iconColor;

/** 文字颜色，默认白色 */
+ (void)setTextColor:(UIColor *)textColor;

/** 文字大小，默认15 */
+ (void)setFontSize:(CGFloat)fontSize;

/** 恢复默认配置 */
+ (void)resetConfig;

```

[https://github.com/remember17/WHToast](https://github.com/remember17/WHToast)