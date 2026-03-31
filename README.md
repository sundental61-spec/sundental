import React, { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";

// NOTE: Replace phone + WhatsApp link, images, and texts with real data.
const WHATSAPP = "https://wa.me/355XXXXXXXXX";

function Navbar({ onBook }) {
  return (
    <nav className="flex justify-between items-center px-6 md:px-10 py-4 shadow-sm sticky top-0 bg-white z-50">
      <h1 className="text-xl font-bold text-blue-600">Sun Dental</h1>
      <div className="hidden md:flex gap-6 text-sm">
        <a href="#services">Services</a>
        <a href="#results">Results</a>
        <a href="#about">About</a>
        <a href="#reviews">Reviews</a>
        <a href="#pricing">Pricing</a>
        <a href="#faq">FAQ</a>
        <a href="#contact">Contact</a>
      </div>
      <button onClick={onBook} className="bg-blue-600 text-white px-4 py-2 rounded-xl">Book Now</button>
    </nav>
  );
}

function Hero({ onBook }) {
  return (
    <section className="py-24 px-6 text-center bg-gradient-to-br from-blue-50 to-white">
      <motion.h1 initial={{ opacity: 0, y: 40 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6 }} className="text-5xl md:text-6xl font-bold mb-6">
        Smile With Confidence
      </motion.h1>
      <p className="text-lg mb-8 max-w-xl mx-auto">
        Premium, pain-free dentistry in Tirana. Advanced technology. Natural, long-lasting results.
      </p>
      <div className="flex justify-center gap-4">
        <button onClick={onBook} className="bg-blue-600 text-white px-6 py-3 rounded-2xl shadow hover:scale-105 transition">Book Appointment</button>
        <a href={WHATSAPP} className="border border-blue-600 px-6 py-3 rounded-2xl hover:bg-blue-50">WhatsApp</a>
      </div>
      <p className="mt-6 text-sm text-gray-500">Free consultation • Same-day treatments available</p>
    </section>
  );
}

function TrustBar() {
  return (
    <section className="bg-gray-100 py-6 text-center text-sm">
      <p>✔ Certified Dentists • ✔ Advanced Technology • ✔ 5★ Patient Experience • ✔ Warranty Options</p>
    </section>
  );
}

function Services() {
  const data = [
    { title: "Dental Implants", desc: "Permanent solution for missing teeth." },
    { title: "Veneers", desc: "Hollywood smile design in few visits." },
    { title: "Teeth Whitening", desc: "Safe, fast brightness." },
    { title: "Orthodontics", desc: "Clear aligners & modern braces." },
    { title: "General Dentistry", desc: "Complete oral care." },
  ];
  return (
    <section id="services" className="py-20 px-6 max-w-6xl mx-auto">
      <h2 className="text-3xl font-semibold text-center mb-12">Our Services</h2>
      <div className="grid md:grid-cols-3 gap-8">
        {data.map((s) => (
          <motion.div key={s.title} whileHover={{ scale: 1.05 }} className="p-6 bg-white rounded-2xl shadow">
            <h3 className="text-xl font-semibold mb-2">{s.title}</h3>
            <p className="text-sm text-gray-600">{s.desc}</p>
          </motion.div>
        ))}
      </div>
    </section>
  );
}

function Results() {
  return (
    <section id="results" className="py-20 px-6 text-center">
      <h2 className="text-3xl font-semibold mb-10">Smile Transformations</h2>
      <div className="grid md:grid-cols-3 gap-6 max-w-5xl mx-auto">
        {[1,2,3,4,5,6].map((i) => (
          <div key={i} className="bg-gray-200 h-48 rounded-xl flex items-center justify-center text-gray-500">Before / After</div>
        ))}
      </div>
    </section>
  );
}

function About() {
  return (
    <section id="about" className="bg-blue-50 py-20 px-6 text-center">
      <h2 className="text-3xl font-semibold mb-6">Why Choose Sun Dental?</h2>
      <p className="max-w-2xl mx-auto text-gray-700">
        We combine elite dental expertise with cutting-edge technology to deliver pain-free, natural results. Every treatment is personalized for long-term health and confidence.
      </p>
    </section>
  );
}

function Testimonials() {
  const [index, setIndex] = useState(0);
  const data = [
    "Life-changing smile!",
    "Professional, modern clinic!",
    "Best experience in Tirana!",
  ];
  return (
    <section id="reviews" className="bg-gray-50 py-20 px-6 text-center">
      <h2 className="text-3xl font-semibold mb-10">What Patients Say</h2>
      <div className="max-w-xl mx-auto">
        <AnimatePresence mode="wait">
          <motion.div key={index} initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} className="p-6 bg-white rounded-2xl shadow">
            <p>"{data[index]}"</p>
          </motion.div>
        </AnimatePresence>
        <div className="flex justify-center gap-3 mt-4">
          {data.map((_, i) => (
            <button key={i} onClick={() => setIndex(i)} className={`w-3 h-3 rounded-full ${i===index?"bg-blue-600":"bg-gray-300"}`} />
          ))}
        </div>
      </div>
    </section>
  );
}

function Pricing({ onBook }) {
  const plans = [
    { name: "Consultation", price: "Free", features: ["Full check", "Treatment plan"] },
    { name: "Whitening", price: "€99+", features: ["1 session", "Safe gel"] },
    { name: "Implants", price: "€XXX", features: ["Premium implant", "Warranty"] },
  ];
  return (
    <section id="pricing" className="py-20 px-6 text-center">
      <h2 className="text-3xl font-semibold mb-10">Pricing & Offers</h2>
      <div className="grid md:grid-cols-3 gap-6 max-w-5xl mx-auto">
        {plans.map((p) => (
          <div key={p.name} className="p-6 bg-white rounded-2xl shadow">
            <h3 className="text-xl font-semibold">{p.name}</h3>
            <p className="text-2xl my-4">{p.price}</p>
            <ul className="text-sm mb-4">
              {p.features.map((f,i)=>(<li key={i}>• {f}</li>))}
            </ul>
            <button onClick={onBook} className="bg-blue-600 text-white px-4 py-2 rounded-xl">Book</button>
          </div>
        ))}
      </div>
    </section>
  );
}

function FAQ() {
  const [open, setOpen] = useState(null);
  const items = [
    { q: "Is treatment painful?", a: "We use modern pain-free techniques." },
    { q: "Do you offer guarantees?", a: "Yes, depending on treatment." },
    { q: "How fast can I book?", a: "Often same-day or next-day." },
  ];
  return (
    <section id="faq" className="py-20 px-6 max-w-3xl mx-auto">
      <h2 className="text-3xl font-semibold text-center mb-10">FAQ</h2>
      {items.map((item,i)=>(
        <div key={i} className="mb-4 border-b pb-2">
          <button onClick={()=>setOpen(open===i?null:i)} className="w-full text-left font-medium">{item.q}</button>
          {open===i && <p className="text-sm text-gray-600 mt-2">{item.a}</p>}
        </div>
      ))}
    </section>
  );
}

function Contact({ onSubmit }) {
  return (
    <section id="contact" className="py-20 px-6 max-w-4xl mx-auto">
      <h2 className="text-3xl font-semibold text-center mb-10">Contact Us</h2>
      <form onSubmit={onSubmit} className="grid gap-4">
        <input required className="border p-3 rounded-xl" placeholder="Name" />
        <input required className="border p-3 rounded-xl" placeholder="Phone" />
        <textarea className="border p-3 rounded-xl" placeholder="Message" />
        <button className="bg-blue-600 text-white py-3 rounded-xl">Send Request</button>
      </form>
      <iframe title="map" className="w-full h-64 mt-8 rounded-xl" src="https://maps.google.com/maps?q=Tirana&t=&z=13&ie=UTF8&iwloc=&output=embed" />
    </section>
  );
}

function BookingModal({ open, onClose, onSubmit }) {
  if (!open) return null;
  return (
    <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50">
      <div className="bg-white p-8 rounded-2xl w-full max-w-md">
        <h3 className="text-xl font-semibold mb-4">Book Appointment</h3>
        <form onSubmit={onSubmit} className="grid gap-3">
          <input required className="border p-2 rounded" placeholder="Name" />
          <input required className="border p-2 rounded" placeholder="Phone" />
          <button className="bg-blue-600 text-white py-2 rounded">Confirm</button>
        </form>
        <button onClick={onClose} className="mt-4 text-sm">Close</button>
      </div>
    </div>
  );
}

export default function SunDentalWebsite() {
  const [open, setOpen] = useState(false);

  const handleSubmit = (e) => {
    e.preventDefault();
    alert("Request sent! We will contact you shortly.");
  };

  return (
    <div className="font-sans text-gray-800 bg-white">

      {/* Sticky Actions */}
      <div className="fixed bottom-4 right-4 flex flex-col gap-3 z-50">
        <a href={WHATSAPP} target="_blank" className="bg-green-500 text-white px-4 py-3 rounded-full shadow-lg">WhatsApp</a>
        <button onClick={() => setOpen(true)} className="bg-blue-600 text-white px-4 py-3 rounded-full shadow-lg">Book</button>
      </div>

      <Navbar onBook={() => setOpen(true)} />
      <Hero onBook={() => setOpen(true)} />
      <TrustBar />
      <Services />
      <Results />
      <About />
      <Testimonials />
      <Pricing onBook={() => setOpen(true)} />
      <FAQ />
      <Contact onSubmit={handleSubmit} />

      <BookingModal open={open} onClose={() => setOpen(false)} onSubmit={handleSubmit} />

      <footer className="bg-gray-900 text-white py-8 text-center">
        <p>Sun Dental • Kodra e Diellit 2, Tirana</p>
      </footer>

    </div>
  );
}
