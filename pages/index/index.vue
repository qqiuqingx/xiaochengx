<template>
	<view class="container">
		<v-tabs v-model="current" :tabs="tabs" @change="changeTab" class="tab"></v-tabs>
		<view class="coupon" ref="coupon">
			<view class="item" v-for="(v, i) in couponList" @click="toCoupon(i)" :key="i">
				<view class="top">
					<view class="left">
						<view class="content">
							<image :src="v.icon" class="icon" mode="widthFix" />
							<view class="name">{{ v.name }}</view>
						</view>
						<view class="text" v-if="v.type == 1">天天可领</view>
						<view class="text" v-else-if="v.type == 2">限时秒杀</view>
					</view>
					<view class="right">免费领取</view>
				</view>
				<view class="bottom"><image :src="v.bannerPic" mode="widthFix" /></view>
			</view>
		</view>
	</view>

</template>

<script>
export default {
	data() {
		return {
			current: 0,
			tabs: [
				{
					icon: '/static/all.png',
					text: '全部',
					tabId: 0,
				},
				// {
				// 	icon: '/static/ele.png',
				// 	text: '饿了么',
				// 	tabId: 1,
				// },
				// {
				// 	icon: '/static/meituan.png',
				// 	text: '美团',
				// 	tabId: 2,
				// }
				// {
				// 	icon: '/static/11.png',
				// 	text: '双十一',
				// 	tabId: 5,
				// },
				// {
				// 	icon: '/static/jd.png',
				// 	text: '京东',
				// 	tabId: 3,
				// },
				// {
				// 	icon: '/static/vip.png',
				// 	text: 'VIP会员',
				// 	tabId: 4,
				// }
			],
			couponList: [],
			coupons: [
				{
					name: '饿了么红包',
					icon: '/static/coupon/ele.png',
					bannerPic: '/static/coupon/ele_banner.png',
					url: 'https://s.click.ele.me/frZOjvu',
					type: 1,
					tabId: 1,
					minapp: {
						appid: 'wxece3a9a4c82f58c9',
						// path: 'pages/sharePid/web/index?scene=https://s.click.ele.me/wR9ecuu'
						 path: 'pages/sharePid/web/index?scene=s.click.ele.me%2F2pqTEuu'
					}
				},
				{
					name: '饿了么果蔬',
					icon: '/static/coupon/ele.png',
					bannerPic: '/static/coupon/ele_guosu.png',
					url:'https://s.click.ele.me/RpRFhvu',
					type: 1,
					tabId: 1,
					minapp: {
						appid: 'wxece3a9a4c82f58c9',
						path: 'pages/sharePid/web/index?scene=s.click.ele.me%2FTSfyUuu'
					}
				},
				{
					name: '美团外卖红包',
					icon: '/static/coupon/meituan.png',
					bannerPic: '/static/coupon/meituan_banner.png',
					url:'https%3A%2F%2Frunion.meituan.com%2Furl%3Fkey%3D004dc473bbeeeb1a329035aa769645b1%26url%3Dhttps%253A%252F%252Fi.meituan.com%252Fawp%252Fhfe%252Fblock%252Fa945391288b790d558b7%252F78716%252Findex.html%253Fappkey%253D004dc473bbeeeb1a329035aa769645b1%253A00940904%26sid%3D00940904&f_token=1&f_userId=1',
					type: 1,
					tabId: 2,
					minapp: {
						appid: 'wxde8ac0a21135c07d',
						//path: '/index/pages/h5/h5?weburl=https%3A%2F%2Frunion.meituan.com%2Furl%3Fkey%3D004dc473bbeeeb1a329035aa769645b1%26url%3Dhttps%3A%2F%2Fi.meituan.com%2Fawp%2Fhfe%2Fblock%2Fa945391288b790d558b7%2F78716%2Findex.html%3F%0Aappkey%3D004dc473bbeeeb1a329035aa769645b1%26sid%3D000940904%26f_token%3D1%26f_userId%3D1'
						path: '/index/pages/h5/h5?lch=mhqIykekFEV63u81zLSTaQViQ&noshare=1&f_userId=0&f_openId=0&f_token=1&weburl=https%3A%2F%2Fact.meituan.com%2Fclover%2Fpage%2Fadunioncps%2Fshare_coupon%3FutmSource%3D56020%26utmMedium%3D3D52DEF4438AE63F0FBF09E13E5B1B8E%26promotionId%3D22073%26activity%3DOwMkGzn6oK'
					}},
					// {
					// 	name: '美团生鲜',
					// 	icon: '/static/coupon/meituan.png',
					// 	bannerPic: '/static/coupon/20201108190015.png',
					// 	url:'https://act.meituan.com/clover/page/adunioncps/share_coupon?utmSource=56020&utmMedium=3D52DEF4438AE63F0FBF09E13E5B1B8E&promotionId=22073&activity=Lj7hGmmCBO',
					// 	type: 0,
					// 	tabId: 3,
					// 	// minapp: {
					// 	// 	appid: 'wxde8ac0a21135c07d',
					// 	// 	path: '/index/pages/h5/h5?weburl=mhqIykekFEV63u81zLSTaQViQ&noshare=1&f_userId=0&f_openId=0&f_token=1&weburl=https%3A%2F%2Fact.meituan.com%2Fclover%2Fpage%2Fadunioncps%2Fshare_coupon%3FutmSource%3D56020%26utmMedium%3D3D52DEF4438AE63F0FBF09E13E5B1B8E%26promotionId%3D22073%26activity%3DOwMkGzn6oK'
					// 	// }
					// },
				// },
				// {
				// 	name: '爱奇艺会员',
				// 	icon: '/static/coupon/vip.png',
				// 	bannerPic: '/static/coupon/vip_banner.png',
				// 	url:'https://p.pinduoduo.com/VJ7bHo5d',
				// 	type: 2,
				// 	tabId: 4
				// },
				// {
				// 	name: '三只松鼠大礼包',
				// 	icon: '/static/coupon/jd.png',
				// 	bannerPic: '/static/coupon/sanzhisongshu.png',
				// 	url:'https://u.jd.com/tFDejq',
				// 	type: 0,
				// 	tabId: 3
				// },
				// {
				// 	name: '饿了么果蔬',
				// 	icon: '/static/coupon/ele.png',
				// 	bannerPic: '/static/coupon/ele_guosu.png',
				// 	url:'https://s.click.ele.me/RpRFhvu',
				// 	type: 1,
				// 	tabId: 1,
				// 	minapp: {
				// 		appid: 'wxece3a9a4c82f58c9',
				// 		path: 'pages/sharePid/web/index?scene=https://s.click.ele.me/I4Yacuu'
				// 	}
				// },
				// {
				// 	name: '抽红包立减',
				// 	icon: '/static/11.png',
				// 	bannerPic: '/static/coupon/11.jpg',
				// 	url:'https://s.click.taobao.com/Gcs9vuu',
				// 	type: 2,
				// 	tabId: 5
				// },
			]
		};
	},
	onLoad(e) {
		//#ifdef H5
		let tabId = this.$route.query.tabId ? parseInt(this.$route.query.tabId) : 0
		//#endif
		//#ifdef MP-WEIXIN
		let tabId = e.tabId ? parseInt(e.tabId) : 0
		//#endif
		for(let i in this.tabs){
			if(tabId == this.tabs[i].tabId){
				this.current = parseInt(i)
			}
		}
		this.changeTab(this.current)
	},
	onShareAppMessage(res) {
		return {
			title: '美团饿了么大额红包，每日可领',
			path: '/pages/index/index'
		}
	},
	methods: {
		changeTab(index) {
			console.log('当前选中的项——1：' + index);
			this.couponList = []
			uni.showLoading({
			    title: '获取优惠中'
			});
			if(index == 0){
				this.couponList = this.coupons
			}else{
				for(let i in this.coupons){
					if(this.coupons[i].tabId == this.tabs[index].tabId){
						this.couponList.push(this.coupons[i])
					}
				}
			}
			//#ifdef H5
			this.$nextTick(() => {
				this.$refs.coupon.scrollTop= 0;
			})
			//#endif
			setTimeout(() => {
				uni.hideLoading()
			}, 500)
		},
		toCoupon(i){
			console.log(this.couponList[i],'123321')
			//h5
			//#ifdef H5
			window.location.href = this.couponList[i].url
			//#endif
			//微信小程序
			//#ifdef MP-WEIXIN
			if(this.couponList[i].minapp){
				console.log("进入小程序判断")
				wx.navigateToMiniProgram({
				  appId: this.couponList[i].minapp.appid,
				  path: this.couponList[i].minapp.path,
				  success(res) {
					// 打开成功
				  }
				})
			}
			//#endif
		}
	}
};
</script>

<style lang="scss">
page {
	background-color: #f8f8f8;
}
.container {
	font-size: 14px;
	line-height: 24px;
	position: relative;
	.tab {
		position: fixed;
		top: var(--window-top);
		left: 0;
		z-index: 9999;
	}
	.coupon {
		padding-top: 200rpx;
		.item {
			background-color: #ffffff;
			margin: 30rpx;
			border-radius: 10rpx;
			padding: 0 30rpx 30rpx 30rpx;
			.top {
				height: 116rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.left {
					height: 116rpx;
					width: 400rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;
					.content {
						width: 100%;
					}
					.icon {
						display: inline-block;
						vertical-align: bottom;
						width: 52rpx;
						height: auto;
					}
					.name {
						text-align: left;
						display: inline-block;
						vertical-align: bottom;
						font-size: 34rpx;
						color: #000;
						line-height: 50rpx;
						font-weight: bold;
						margin-left: 15rpx;
					}
					.text {
						width: 150rpx;
						height: 38rpx;
						line-height: 38rpx;
						text-align: center;
						font-size: 24rpx;
						color: #61300e;
						background: linear-gradient(90deg, #f9db8d, #f8d98a);
						border-radius: 6rpx;
					}
				}
				.right {
					width: 170rpx;
					height: 60rpx;
					border-radius: 30rpx;
					background: linear-gradient(90deg, #ec6f43, #ea4a36);
					color: #fff;
					font-size: 28rpx;
					line-height: 60rpx;
					text-align: center;
				}
			}
			.bottom {
				height: auto;
				width: 100%;
				image {
					display: block;
					width: 100%;
					height: auto;
				}
			}
		}
	}
}
</style>